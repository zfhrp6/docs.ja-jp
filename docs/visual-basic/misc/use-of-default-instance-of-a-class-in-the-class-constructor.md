---
title: "クラス コンストラクター内のクラスの既定のインスタンスを使用すると、無限の再帰呼び出しを引き起こす能性があります。 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# クラス コンストラクター内のクラスの既定のインスタンスを使用すると、無限の再帰呼び出しを引き起こす能性があります。
クラスの既定のインスタンスは、クラス コンストラクターで使用されています。 これは、無限ループとも呼ばれる、無限の再帰呼び出しを引き起こす可能性があります。  
  
### このエラーを解決するには  
  
-   クラス コンストラクターから、既定のインスタンスを削除します。  
  
## 参照  
 [ビルド内にありません: コンストラクタとデストラクタの使用方法](http://msdn.microsoft.com/ja-jp/548eebe1-86c4-4377-b2f5-447cb8be3d90)