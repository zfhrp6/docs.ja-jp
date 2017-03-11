---
title: "Troubleshooting Arrays (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "troubleshooting arrays"
  - "arrays [Visual Basic], initialization errors"
  - "troubleshooting Visual Basic, arrays"
  - "arrays [Visual Basic], compilation errors"
  - "arrays [Visual Basic], declaration errors"
  - "arrays [Visual Basic], troubleshooting"
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Troubleshooting Arrays (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ここでは、配列を使用する際に起きる一般的な問題についていくつか説明します。  
  
## 配列の宣言と初期化に関するコンパイル エラー  
 配列の宣言、作成、初期化に関する規則をよく理解していないと、コンパイル エラーが発生します。  代表的なエラーの原因を次に示します。  
  
-   配列変数の宣言の中で次元のサイズを指定した後に [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) 句を記述している。  この種の無効な宣言の例を次に示します。  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   ジャグ配列のトップ レベル配列よりも大きい次元サイズを指定している。  この種の無効な宣言の例を次に示します。  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   要素値を指定するときに `New` キーワードを省略している。  この種の無効な宣言の例を次に示します。  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   中かっこ \(`{}`\) を使用せずに `New` 句を指定している。  この種の無効な宣言の例を次に示します。  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## 配列の範囲外へのアクセス  
 配列の初期化プロセスでは、配列の各次元に上限と下限を割り当てます。  配列の要素にアクセスするときには、それぞれの次元について有効なインデックスまたは添字を指定する必要があります。  指定したインデックスが下限より小さいか、上限より大きい場合は、<xref:System.IndexOutOfRangeException> 例外が発生します。  コンパイラはこのようなエラーを検出できないので、実行時にエラーが発生します。  
  
### 範囲の確認  
 別のコンポーネントからプロシージャ引数などの形でコードに配列が渡される場合は、その配列のサイズや各次元のサイズはわかりません。  配列内の要素にアクセスするときには、事前に配列の各次元の上限を調べる必要があります。  配列が [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の `New` 句以外の方法で作成されている場合は、下限が 0 でない可能性もあるので、下限も調べておいた方が安全です。  
  
### 次元の指定  
 多次元配列の範囲を調べるときには、次元の指定方法に注意してください。  <xref:System.Array.GetLowerBound%2A> メソッドおよび <xref:System.Array.GetUpperBound%2A> メソッドの `dimension` パラメーターは 0 から始まりますが、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の <xref:Microsoft.VisualBasic.Information.LBound%2A> 関数および <xref:Microsoft.VisualBasic.Information.UBound%2A> 関数の `Rank` パラメーターは 1 から始まります。  
  
## 参照  
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)