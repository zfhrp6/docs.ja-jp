---
title: "正しくないパターン文字列 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# 正しくないパターン文字列
検索の `Like` 演算で指定されているパターン文字列が正しくありません。  
  
### このエラーを解決するには  
  
1.  リスト式に使用できる文字を確認します。  
  
2.  パターン範囲の指定で、`[a-z]` のように、範囲の開始文字が終了文字より小さいことを確認します。  
  
3.  パターン範囲の指定で、`[a--z]` のように、複数のハイフンが続けて指定されていないことを確認します。  
  
4.  パターン範囲を右角かっこで終了します。  
  
## 参照  
 [Like Operator](../../visual-basic/language-reference/operators/like-operator.md)