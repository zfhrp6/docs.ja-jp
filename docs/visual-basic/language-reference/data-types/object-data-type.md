---
title: "Object Data Type | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Object"
  - "vb.Variant"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "object variables, Object type"
  - "data types [Visual Basic], assigning"
  - "Object data type"
  - "Object data type, reference"
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Object Data Type
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

オブジェクトを参照するアドレスを格納します。  オブジェクト \(`Object`\) 変数には、任意の参照型 \(文字列、配列、クラス、またはインターフェイス\) を割り当てることができます。  また、オブジェクト型 \(`Object`\) の変数は、任意の値型 \(数値、ブール型 \(`Boolean`\)、char 型 \(`Char`\)、日付型 \(`Date`\)、構造体、または列挙型\) のデータを参照できます。  
  
## 解説  
 オブジェクト型 \(`Object`\) は、任意のデータ型のデータをポイントできます。これにはアプリケーションが認識する任意のオブジェクト インスタンスも含まれます。  オブジェクト型 \(`Object`\) は、コンパイル時に変数がどのデータ型をポイントするかわからない場合に使用します。  
  
 `Object` の既定値は `Nothing` \(null 参照\) です。  
  
## データ型  
 すべてのデータ型の変数、定数、または式を、オブジェクト型 \(`Object`\) の変数に代入できます。  `Object` 変数が現在参照しているデータ型を調べるには、<xref:System.Type?displayProperty=fullName> クラスの <xref:System.Type.GetTypeCode%2A> メソッドを使用します。  次に例を示します。  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 オブジェクト型 \(`Object`\) は参照型です。  ただし、`Object` 変数が値型のデータを参照する場合は、値型として扱われます。  
  
## Storage  
 `Object` 変数はどのデータ型を参照する場合でも、データの値そのものを格納するのではなく、値へのポインターを格納します。  このポインターはコンピューターのメモリ内で常に 4 バイトを占めますが、変数の値を表すデータの記憶領域は別に割り当てられます。  コードはポインターを使用してデータを探すため、値型を保持するオブジェクト型 \(`Object`\) の変数は、明示的に型指定された変数よりも多少アクセスに時間がかかります。  
  
## プログラミングのヒント  
  
-   **相互運用の考慮事項。**たとえば Automation オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントを使用する場合は、他の環境のポインター型に Visual Basic のオブジェクト型 \(`Object`\) との互換性がないことを頭に入れておく必要があります。  
  
-   **パフォーマンス**オブジェクト型 \(`Object`\) を使って定義した変数は非常に柔軟であり、あらゆるオブジェクトへの参照を格納できます。  しかし、このような変数からメソッドまたはプロパティを呼び出すと、必ず*遅延バインディング* \(実行時の連結\) が発生してしまいます。  *事前バインディング* \(コンパイル時の連結\) を強制し、パフォーマンスを向上させるには、特定のクラス名を使って変数を宣言するか、または変数を特定のデータ型にキャストする必要があります。  
  
     オブジェクト変数を宣言する場合は、汎用のオブジェクト型 \(`Object`\) 使用するのではなく、たとえば <xref:System.OperatingSystem> など、できるだけ具体的なクラス型を使うようにしてください。  また、<xref:System.Windows.Forms.Control> ではなく <xref:System.Windows.Forms.TextBox> など、最も具体的なクラスを使用してください。そうすることで、クラスのプロパティやメソッドにアクセスできます。  通常、**\[オブジェクト ブラウザー\]** の **\[クラス\]** ボックスから、使用できるクラス名を探すことができます。  
  
-   **拡大変換。**すべてのデータ型とすべての参照型が、オブジェクト型 \(`Object`\) に拡大変換されます。  これは、<xref:System.OverflowException?displayProperty=fullName> エラーを発生させることなく、任意の型をオブジェクト型 \(`Object`\) に変換できることを意味します。  
  
     ただし、値型とオブジェクト型 \(`Object`\) の間で変換を行うと、Visual Basic は*ボックス化*および*ボックス化解除*と呼ばれる処理を実行するため、実行時間が長くなります。  
  
-   **型文字。** SByte 型 \(`Object`\) にはリテラルの型文字も、識別子の型文字もありません。  
  
-   **Framework のデータ型。**.NET Framework において対応する型は、<xref:System.Object?displayProperty=fullName> クラスです。  
  
## 使用例  
 オブジェクト インスタンスをポイントする `Object` 変数の例は、次のようになります。  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## 参照  
 <xref:System.Object>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [How to: Determine Whether Two Objects Are Related](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [How to: Determine Whether Two Objects Are Identical](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)