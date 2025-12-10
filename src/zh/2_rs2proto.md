# 互联网重构周记 : 2 - 基于 rust 包生成 grpc 服务

在 《 互联网重构周记：1 - 开篇 》 中，我阐述了后端服务的实现思路。

基于 rust 文件 生成 protobuf 文件


## cookie 设置

修改响应头

自动设置设备 id，这样就不用设置 cookie

设备 id 分为 id，时间，签名 3 部分，如果时间超过 1 周，会更新设置新的 cookie 签名

如果时间超过 2 个年，认为 cookie 无效

## 模块递归生成

## 函数参数必须是基本类型或是基本类型的 Vec

## 返回值可以是结构体

## rust 代码生成 grpc 的 protobuf

## volo-grpc 胶水

## 用户系统设计

`device_id` → `user_id`


进程内缓存, 10 秒没人访问就过期，客户端会带上 user_id, 这样切换用户，服务器会重新认证

use moka::sync::Cache;
use std::thread;
use std::time::Duration;

fn main() {
    // 使用 CacheBuilder 构建缓存
    // 设置 time_to_idle 为 10 秒
    let cache: Cache<String, String> = Cache::builder()
        .time_to_idle(Duration::from_secs(10))
        .build();

    // 插入一个键值对
    cache.insert("my_key".to_string(), "my_value".to_string());
    println!("插入了键 'my_key'");