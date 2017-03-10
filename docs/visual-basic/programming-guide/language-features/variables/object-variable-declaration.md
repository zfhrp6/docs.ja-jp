---
title: "Object Variable Declaration (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "early binding"
  - "declarations, class"
  - "classes [Visual Basic], declaring"
  - "binding, late and early"
  - "object variables, declaring"
  - "variables [Visual Basic], object"
  - "declaring variables, object variables"
  - "declaring classes"
  - "late binding"
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 33
---
# Object Variable Declaration (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

オブジェクト変数を宣言する場合は、通常の宣言ステートメントを使用します。  データ型については、`Object` \(つまり、[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)\) か、オブジェクトの作成元となる、より具体的なクラスのいずれかを指定します。  
  
 変数を `Object` として宣言することは、<xref:System.Object?displayProperty=fullName> として宣言するのと同じことです。  
  
 特定のオブジェクト クラスを使って宣言した変数は、そのクラスおよびそのクラスが継承している各クラスによって公開されている、すべてのメソッドとプロパティにアクセスできます。  <xref:System.Object> を指定して変数を宣言した場合、`Option Strict Off` を指定して遅延バインディングを有効にしていない限り、<xref:System.Object> クラスのメンバーにのみアクセスできます。  
  
## 宣言の構文  
 オブジェクト変数を宣言するには、次の構文を使用します。  
  
```  
Dim variablename As [New] { objectclass | Object }  
```  
  
 また、宣言には [Public](../../../../visual-basic/language-reference/modifiers/public.md)、[Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)、`Protected Friend`、[Private](../../../../visual-basic/language-reference/modifiers/private.md)、[Shared](../../../../visual-basic/language-reference/modifiers/shared.md)、または [Static](../../../../visual-basic/language-reference/modifiers/static.md) も指定できます。  たとえば、次の例のような宣言も有効です。  
  
```  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## 遅延バインディングと事前バインディング  
 場合によっては、コードを実行するまで具体的なクラスがわからないことがあります。  このような場合は、オブジェクト型 \(`Object`\) を使ってオブジェクト変数を宣言する必要があります。  これによって任意の型のオブジェクトに対応する汎用の参照が作成され、実行時に具体的なクラスが割り当てられます。  これは、*遅延バインディング*と呼ばれます。  遅延バインディングを行う場合、実行に必要な時間が長くなります。  また、遅延バインディングでは、直近に代入したクラスのメソッドおよびプロパティにしかコードからアクセスできません。  そのため、別のクラスのメンバーにアクセスしようとするコードがあると、実行時エラーが発生する可能性があります。  
  
 コンパイル時に具体的なクラスがわかっている場合は、そのクラスを指定してオブジェクト変数を宣言します。  これは、*事前バインディング*と呼ばれます。  事前バインディングでは、パフォーマンスが向上し、コードから特定のクラスのすべてのメソッドおよびプロパティに確実にアクセスできます。  上の例の宣言では、変数 `objA` がクラス <xref:System.Windows.Forms.Label?displayProperty=fullName> のオブジェクトだけを使用する場合は、宣言で `As System.Windows.Forms.Label` を指定する必要があります。  
  
### 事前バインディングの利点  
 オブジェクト変数を特定のクラスとして宣言することには、次のようにいくつかの利点があります。  
  
-   自動的な型チェック  
  
-   特定のクラスのすべてのメンバーに対するアクセスの保証  
  
-   コード エディターにおける Microsoft IntelliSense のサポート  
  
-   コードの読みやすさの向上  
  
-   コードのエラーの減少  
  
-   実行時ではなくコンパイル時のエラー検出  
  
-   コードの実行の高速化  
  
## オブジェクト変数のメンバーへのアクセス  
 `Option Strict` が `On` になっている場合、オブジェクト変数がアクセスできるのは、その変数の宣言時に指定したクラスのメソッドとプロパティだけです。  次に例を示します。  
  
```  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 この例の場合、`p` で使用できるのは <xref:System.Object> クラス自身のメンバーだけです。`Left` プロパティは含まれません。  一方、`q` は、<xref:System.Windows.Forms.Label> 型として宣言されているので、<xref:System.Windows.Forms> 名前空間の <xref:System.Windows.Forms.Label> クラスのすべてのメソッドとプロパティを使用できます。  
  
## オブジェクト変数の柔軟性  
 継承階層のオブジェクトを使用する場合に、どのクラスを使ってオブジェクト変数を宣言するかを選択できます。  クラスを選択するときに、オブジェクトを代入する場合の柔軟性とクラスのメンバーへのアクセスとのバランスを考慮する必要があります。  たとえば、<xref:System.Windows.Forms.Form?displayProperty=fullName> クラスに至る継承階層は次のようになります。  
  
 <xref:System.Object>  
  
 `` <xref:System.ComponentModel.Component>  
  
 `` <xref:System.Windows.Forms.Control>  
  
 `` <xref:System.Windows.Forms.ScrollableControl>  
  
 `` <xref:System.Windows.Forms.ContainerControl>  
  
 `` <xref:System.Windows.Forms.Form>  
  
 たとえば、<xref:System.Windows.Forms.Form> クラスを継承する `specialForm` というフォーム クラスをアプリケーションで定義するとします。  次の例のように宣言すると、`specialForm` だけを参照するオブジェクト変数を宣言できます。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 上の例の宣言では、変数 `nextForm` を `specialForm` クラスのオブジェクトに制限していますが、`specialForm` のすべてのメソッドとプロパティに加え、`specialForm` が継承しているすべてのクラスのすべてのメンバーも `nextForm` から使用できます。  
  
 次の例に示すように、オブジェクト変数を <xref:System.Windows.Forms.Form> 型として宣言すると、汎用性が高くなります。  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
 上の例の宣言では、アプリケーション内の任意のフォームを `anyForm` に代入できます。  ただし、`anyForm` は <xref:System.Windows.Forms.Form> クラスのすべてのメンバーにアクセスできますが、`specialForm` など特定のフォーム用に定義された追加のメソッドやプロパティは使用できません。  
  
 基本クラスのメンバーはすべて派生クラスで使用できますが、派生クラスで追加されたメンバーを基本クラスで使用することはできません。  
  
## 参照  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [How to: Declare an Object Variable and Assign an Object to It in Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)   
 [How to: Access Members of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)