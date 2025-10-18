# 互联网重构周记 : 2 - 基于 rust 包生成 grpc 服务


## 递归生成

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