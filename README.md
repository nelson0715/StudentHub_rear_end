# StudentHub 專案 注(以下部分使用ChatGPT生成 架構圖自己畫的!) 老師抱歉作業沒有寫出來,我把我會的寫完

這是一個基於 **MVC 架構**、**前後端分離** 的專案，實現了完整的 CRUD 功能。專案整合了 **前端**、**後端** 和 **資料庫**，並提供了 API 端點來操作學生資料。

## 專案網址

- **前端**: [GitHub - StudentHub Frontend](https://github.com/nelson0715/StudentHub_front_end)
- **後端**: [GitHub - StudentHub Backend](https://github.com/nelson0715/StudentHub_rear_end)

## 功能說明

- **Create**: 新增學生資料（使用 `insertOne` 操作）
- **Read**: 查詢所有學生資料（使用 `findAll` 操作）
- **Update**: 更新學生資料（使用 `updateNameById` 操作）
- **Delete**: 刪除學生資料（使用 `deleteById` 操作）

## 安裝與執行指引

### 環境需求

- **前端開發**: React + TypeScript
- **後端開發**: Node.js + Express
- **資料庫**: MongoDB
- **API 測試工具**: Postman
- **安裝套件管理工具**: npm

#### 查詢學生資料(Read)
* GET 方法
* 描述 : 根據學生的缺席次數、姓名或座號查詢資料。

#### 新增學生資料(Create)
* POST

Body :
```typescript
{
    "userName": "tkuim0425",
    "name": "王大明",
    "sid": "51",
    "department": "資訊管理學系",
    "grade": "3",
    "class": "C",
    "Email": "411630519@o365.tku.edu.tw"
}
```

(回應)
* 成功 : 
```typescript
{
    "code": 200,
    "message": "",
    "body": {
        "userName": "tkuim0425",
        "name": "大帥哥",
        "sid": "51",
        "department": "資訊管理學系",
        "grade": "3",
        "class": "C",
        "Email": "411630543@o365.tku.edu.tw"
        "_id": "6759b6c52927e07a0ddeb599",
        "__v": 0
    }
}
```

* 失敗 : 
```typescript
{
  "code": 403,
  "message": "student list is full"
}
```
* 或是 : 
```typescript
{
  "code": 500,
  "message": "server error"
}
```
#### 刪除學生資料(Delete)
* DELETE

Body :
```typescript
{
  "userName": "tkuim0425"
}
```

(回應)
* 成功 : 
```typescript
{
  "code": 200,
  "message": "success",
  "body": {
    "userName": "tkuim0425"
  }
}
```

* 失敗 : 
```typescript
{
  "code": 500,
  "message": ""
}
```

#### 更新學生資料(Update)
* PUT

Body :
```typescript
{
  "userName": "tkuim0425",
  "name": "陳庭浩"
}
```

(回應)
* 成功 : 
```typescript
{
  "code": 200,
  "message": "update success",
  "body": {
    "userName": "tkuim0715",
    "name": "廖則宇"
  }
}
```

* 失敗 : 
```typescript
{
  "code": 404,
  "message": "user not found"
}
```

### 架構圖 : 展示前端、後端、資料庫及其互動
![架構圖](123.drawio (1).png)

### 流程圖：描述 CRUD 功能的操作流程。

* 查詢學生: GET=> /api/v1/user/findAll
* 新增學生: POST=> /api/v1/user/insertOne
* 刪除學生: DELETE=> /api/v1/user/deleteById
* 更新學生: PUT=> /api/v1/user/updateNameById

#### 流程解說

1. 用戶操作前端界面：使用者在 React 前端界面上提交表單或點擊按鈕來新增、查詢、更新或刪除學生資料。

2. 前端發送請求：前端使用 Fetch API 向後端的 Express 伺服器發送 HTTP 請求，這些請求可以是 POST、GET、PUT 或 DELETE。

3. 後端路由處理請求：後端根據請求的 URL 和方法，將請求引導到對應的控制器函數。

4. 控制器執行業務邏輯：控制器處理請求，並調用服務層執行具體的業務邏輯，如驗證資料或格式化數據。

5. 服務層與模型交互：服務層負責與資料模型（Model）進行溝通，執行對資料庫的增、刪、改、查操作

6. 資料庫操作：資料模型使用 Mongoose 與 MongoDB 進行實際的資料庫操作，處理資料的新增、查詢、更新或刪除。

7. 結果回傳：資料庫操作完成後，結果會從資料模型回傳到控制器，並最終返回給前端。

8. 前端更新顯示：前端接收後端回傳的數據，並根據回應更新頁面或顯示提示訊息。
