---
title: "GetType Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.GetType"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "GetType operator"
  - "GetType keyword"
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# GetType Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

指定された型の <xref:System.Type> オブジェクトを返します。  <xref:System.Type> オブジェクトにはプロパティ、メソッド、イベントなど、その型に関する情報が含まれています。  
  
## 構文  
  
```  
GetType(typename)  
```  
  
#### パラメーター  
  
|||  
|-|-|  
|パラメーター|Description|  
|`typename`|情報を取得する型の名前を指定します。|  
  
## 解説  
 `GetType` 演算子は、指定された `typename` の <xref:System.Type> オブジェクトを返します。  `typename` には、定義済みの任意の型の名前を渡すことができます。  次に例を示します。  
  
-   `Boolean` や `Date` などの Visual Basic のデータ型  
  
-   <xref:System.ArgumentException?displayProperty=fullName> や <xref:System.Double?displayProperty=fullName> などの .NET Framework のクラス、構造体、モジュール、インターフェイス。  
  
-   アプリケーションで定義したクラス、構造体、モジュール、またはインターフェイス。  
  
-   アプリケーションで定義した配列。  
  
-   アプリケーションで定義したデリゲート。  
  
-   Visual Basic、.NET Framework、またはアプリケーションで定義した列挙体。  
  
 オブジェクト変数の型オブジェクトを取得する場合は、<xref:System.Type.GetType%2A?displayProperty=fullName> メソッドを使用します。  
  
 `GetType` 演算子は次のような場合に使用できます。  
  
-   実行時に、型のメタデータにアクセスする必要がある場合。  <xref:System.Type> オブジェクトには、型のメンバーや配置情報などのメタデータが含まれています。  たとえば、アセンブリに対してリフレクションする場合などにこれが必要になります。  詳細については、「<xref:System.Reflection?displayProperty=fullName>」を参照してください。  
  
-   2 つのオブジェクト参照を比較して、それらが同じ型のインスタンスを参照しているかを確認することがあります。  同じ型のインスタンスを参照している場合、`GetType` は同じ <xref:System.Type> オブジェクトへの参照を返します。  
  
## 使用例  
 `GetType` 演算子の使用例を次に示します。  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## 参照  
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)