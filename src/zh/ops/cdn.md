js0.site


域名托管到 cloudflare，用它的邮件路由，可以收邮件。

然后主域名和泛域名 cname 托管到腾讯云 edgeone 。

腾讯云 edgeone 国内版，只要备案就可以全球加速（包括中国国内），其他 CDN 比如 cloudflare 的中国区加速需要企业版（[$5000 每月起步](https://www.chinafy.com/blog/compare-chinafy-vs-cloudflare-cdn-and-learn-how-enterprises-use-these-solutions-together?utm_source=chatgpt.com#what-are-the-differences-between-cloudflare-global-vs-cloudflare-china)）。


cron 配置上传绑定证书

配置腾讯云泛域名重定向边缘函数 `wildcard-redirect` 如下:

```
addEventListener('fetch', event => {
  event.respondWith(((request) => {
    const url = new URL(request.url), {hostname}=url;
    url.hostname = hostname.slice(hostname.indexOf('.') + 1)
    return new Response(null, {
      headers: { location: url.toString() },
      status: 301
    });
  })(event.request));
});
```

规则配置 不等于 主域名 就 运行