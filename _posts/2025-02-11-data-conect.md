# Data Connect

## Summary
Data Connect 是 Google Firebase 的其中一項產品。在 Firebase 眾多服務中，現有的資料庫產品主要是 Firestore，這是一種非關聯式資料庫，資料結構包括 collections（集合）、documents（文件）與 data（資料）。然而，由於關聯式資料庫的需求仍然相當龐大，Google 開發了一項全新的產品，也就是 Data Connect。

Data Connect 是一種關聯式資料庫，其書寫語法採用 GraphQL，但其底層基礎仍然是 PostgreSQL。值得一提的是，GraphQL 最初是 Facebook 的內部技術，後來被開放為開源項目。相較於 SQL，GraphQL 的語法更為簡單，但靈活性與表達能力可能不如 SQL 那般接近自然語言。

Data Connect 的另一大特色在於其對向量資料的支持。它提供了模型來計算矩陣數值，讓使用者能夠方便地存取與操作向量資料。這一特性使得 Data Connect 在需要處理向量或高維數據的應用場景中，具備極大的優勢。



## Q&A
1. Q：GraphQL 語法的驚嘆號是什麼？
A：代表欄位一定要有值
2. 可以實現Emebedding功能嗎?
A: 可以，只是要開啟Verext ai收費功能。

## 資料夾結構

![image](https://hackmd.io/_uploads/BJKaUh6Nke.png)
- connector.yaml：將 gql 編譯為 js（？
- mutations.gql：新刪修的 GraphQL 語法
- queries.gql：查詢的 GraphQL 語法
- schema：Data Connect 資料庫的資料結構

## Transaction
:::info
Cloud Firestore 支援讀取和寫入資料的不可部分完成作業。在一系列不可分割的作業中，所有作業都會成功，或是全部不予套用。Cloud Firestore 中有兩種原子作業：

交易：交易是一或多個文件上的一組讀取和寫入作業。
批次寫入：批次寫入是指一或多份文件上的一組寫入作業。
:::

- example
```javascript=
import { runTransaction } from "firebase/firestore";

try {
  await runTransaction(db, async (transaction) => {
    const sfDoc = await transaction.get(sfDocRef);
    if (!sfDoc.exists()) {
      throw "Document does not exist!";
    }

    const newPopulation = sfDoc.data().population + 1;
    transaction.update(sfDocRef, { population: newPopulation });
  });
  console.log("Transaction successfully committed!");
} catch (e) {
  console.log("Transaction failed: ", e);
}
```

### 交易失敗
- 交易可能會因下列原因失敗：

    - 交易包含寫入作業後的讀取作業。讀取作業必須一律在任何寫入作業之前執行。
    - 交易讀取在交易外修改的文件。在這種情況下，系統會自動再次執行交易。交易會重試有限次數。交易超出 10 MiB 的最大要求大小上限。
    - 交易大小取決於交易修改的文件和索引項目大小。對於刪除作業，這包括目標文件的大小，以及因應作業而刪除的索引項目大小。

    - 失敗的交易會傳回錯誤，且不會將任何內容寫入資料庫。您不需要復原交易，Cloud Firestore 會自動執行這項作業。

### 實作練習
- https://github.com/learnai2024XD/data-connect-practice

### 參考
- [官方文件](https://firebase.google.com/docs/firestore/manage-data/transactions?hl=zh-tw)
- [官方介紹影片](https://www.youtube.com/watch?v=7OdVatEI85o)
- [Cheat Sheet](https://devhints.io/graphql)
- [範例教學](https://firebase.google.com/codelabs/firebase-dataconnect-web?hl=zh-tw)