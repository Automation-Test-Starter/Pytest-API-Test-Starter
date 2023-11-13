# API doc for demoAPI

- [API doc for demoAPI](#api-doc-for-demoapi)
  - [中文版本](#中文版本)
    - [demo 测试接口](#demo-测试接口)
      - [Get 接口](#get-接口)
      - [Post 接口](#post-接口)
  - [English Version](#english-version)
    - [Introduction of demo test API](#introduction-of-demo-test-api)
      - [Get API](#get-api)
      - [Post API](#post-api)

## 中文版本

### demo 测试接口

#### Get 接口

- HOST: https://jsonplaceholder.typicode.com
- 接口地址：/posts/1
- 请求方式：GET
- 请求参数：无
- 请求头："Content-Type": "application/json; charset=utf-8"
- 请求体：无
- 返回状态码：200
- 返回头："Content-Type": "application/json; charset=utf-8"
- 返回 body：

```json
{
    "userId": 1,
    "id": 1,
    "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
    "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}
```

#### Post 接口

- HOST: https://jsonplaceholder.typicode.com
- 接口地址：/posts
- 请求方式：POST
- 请求参数：无
- 请求头："Content-Type": "application/json; charset=utf-8"
- 请求体：raw json 格式 body 内容如下：

```json
{
    "title": "foo",
    "body": "bar",
    "userId": 1
}
```

- 返回状态码：201
- 返回头："Content-Type": "application/json; charset=utf-8"
- 返回 body：

```json
{
    "title": "foo",
    "body": "bar",
    "userId": 1,
    "id": 101
}
```

## English Version

### Introduction of demo test API

#### Get API

- HOST: https://jsonplaceholder.typicode.com
- API path: /posts/1
- Request method: GET
- Request Parameters: None
- Request header: "Content-Type": "application/json; charset=utf-8"
- Request Body: None
- Response status code: 200
- Response header: "Content-Type": "application/json; charset=utf-8"
- Response body:

```json
{
    "userId": 1,
    "id": 1,
    "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
    "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}
```

#### Post API

- HOST: https://jsonplaceholder.typicode.com
- API path:/posts
- Request method: POST
- Request Parameters: None
- Request header:"Content-Type": "application/json; charset=utf-8"
- Request Body:raw json format
- Request Body:

```json
{
    "title": "foo",
    "body": "bar",
    "userId": 1
}
```

- Response status code: 201
- Response header:"Content-Type": "application/json; charset=utf-8"
- Response body:

```json
{
    "title": "foo",
    "body": "bar",
    "userId": 1,
    "id": 101
}
```
