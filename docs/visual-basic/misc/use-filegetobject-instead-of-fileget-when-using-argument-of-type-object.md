---
title: "型 &#39;Object&#39; の引数を使用する場合は、&#39;FileGet&#39; ではなく &#39;FileGetObject&#39; を使用してください。 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# 型 &#39;Object&#39; の引数を使用する場合は、&#39;FileGet&#39; ではなく &#39;FileGetObject&#39; を使用してください。
`FileGet` メソッドには、型 `Object` の引数が含まれています。 あいまいさを避けるため、`FileGet` の代わりに `FileGetObject` を使用する必要があります。  
  
 `My.Computer.Filesystem` によって提供される機能は、`FileGet` または `FileGetObject` よりも使いやすく、パフォーマンスが優れています。  
  
### このエラーを解決するには  
  
1.  `FileGet` を `FileGetObject` に置き換えます。  
  
2.  `Object` 引数をより具体的な種類にキャストします。  
  
## 参照  
 [ビルド内にありません: FileGetObject 関数](http://msdn.microsoft.com/ja-jp/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)   
 [My.Computer.FileSystem Object](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)