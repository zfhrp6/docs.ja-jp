---
title: "How to: Access Members of an Object (Visual Basic) | Microsoft Docs"
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
  - "members, accessing"
  - "object variables, accessing members"
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How to: Access Members of an Object (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

オブジェクトを参照するオブジェクト変数がある場合、メソッド、プロパティ、フィールド、およびイベントなどのオブジェクトのメンバーで作業を行うことができます。  たとえば、新しい <xref:System.Windows.Forms.Form> オブジェクトを作成した後、<xref:System.Windows.Forms.Control.Text%2A> プロパティを設定したり、または <xref:System.Windows.Forms.Control.Focus%2A> メソッドを呼び出すことができます。  
  
## メンバーへのアクセス  
 オブジェクトのメンバーを参照する変数を使用して、オブジェクトのメンバーにアクセスします。  
  
#### オブジェクトのメンバーにアクセスするには  
  
-   オブジェクト変数名とメンバー名との間で、メンバー アクセス演算子 \(`.`\) を使用します。  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     メンバーが [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) である場合、アクセスするための変数は必要ありません。  
  
## 既知の型のオブジェクトのメンバーへのアクセス  
 コンパイル時にオブジェクトの型がわかっている場合、それを参照している変数に対して、*事前バインディング*を使用できます。  
  
#### コンパイル時に型がわかっているオブジェクトのメンバーにアクセスするには  
  
1.  オブジェクト変数を、変数に割り当てようとしているオブジェクトの型として宣言します。  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form   
    ```  
  
     `Option Strict On` を使用すると、<xref:System.Windows.Forms.Form> オブジェクト \(または <xref:System.Windows.Forms.Form> から派生した型のオブジェクト\) だけを、`extraForm` に割り当てることができます。  <xref:System.Windows.Forms.Form> への `CType` の拡大変換を使用して、クラスまたは構造体が定義されている場合、そのクラスまたは構造体を `extraForm` に割り当てることもできます。  
  
2.  オブジェクト変数名とメンバー名との間で、メンバー アクセス演算子 \(`.`\) を使用します。  
  
    ```  
    extraForm.Show()  
    ```  
  
     `Option Strict` がどのような設定になっていても、<xref:System.Windows.Forms.Form> クラス固有のすべてのメソッドおよびプロパティにアクセスできます。  
  
## 不明な型のオブジェクトのメンバーへのアクセス  
 コンパイル時にオブジェクトの型がわからない場合、それを参照しているすべての変数に対して、*遅延バインディング*を使用する必要があります。  
  
#### コンパイル時に型がわかっていないオブジェクトのメンバーにアクセスするには  
  
1.  オブジェクト変数を [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) として宣言します。  \(変数を `Object` として宣言すると、<xref:System.Object?displayProperty=fullName> として宣言することと同等になります。\)  
  
    ```  
    Dim someControl As Object   
    ```  
  
     `Option Strict On` を使用すると、<xref:System.Object> クラスで定義されたメンバーだけにアクセスできます。  
  
2.  オブジェクト変数名とメンバー名との間で、メンバー アクセス演算子 \(`.`\) を使用します。  
  
    ```  
    someControl.GetType()  
    ```  
  
     オブジェクト変数に割り当てたオブジェクトのメンバーにアクセスできるようにするには、`Option Strict Off` を設定する必要があります。  これを行うと、変数に割り当てたオブジェクトによって、指定されたメンバーが公開されるかどうかをコンパイラは保証できません。  アクセスしようとしたメンバーをオブジェクトが公開しない場合、<xref:System.MemberAccessException> 例外が発生します。  
  
## 参照  
 <xref:System.Object>   
 <xref:System.Windows.Forms.Form>   
 <xref:System.MemberAccessException>   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)