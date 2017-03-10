---
title: "Overloaded Properties and Methods (Visual Basic) | Microsoft Docs"
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
  - "properties [Visual Basic], overloading"
  - "methods [Visual Basic], overloading"
  - "shadowing"
  - "names, multiple procedures with same"
  - "procedures, mulltiples with same name"
  - "classes [Visual Basic], properties"
  - "classes [Visual Basic], methods"
  - "method overloading"
  - "Overloads keyword, overloaded members"
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Overloaded Properties and Methods (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

オーバーロードとは、異なる型の引数を持つ同じ名前のプロシージャ、インスタンス コンストラクター、またはプロパティをクラスに複数作成することです。  
  
## オーバーロードの使用方法  
 別のデータ型を処理するプロシージャに同じ名前を付けるオブジェクト モデルを使用している場合は、特にオーバーロードが有効です。  たとえば、複数のデータ型を表示できるクラスの `Display` プロシージャは、次のようになります。  
  
 [!code-vb[VbVbalrOOP#64](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#64)]  
  
 オーバーロードを利用しない場合は、各プロシージャの動作が同じであっても、次のようにそれぞれに別の名前を付ける必要があります。  
  
 [!code-vb[VbVbalrOOP#65](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#65)]  
  
 オーバーロードを利用すると、使用するデータ型を選択できるようになるため、プロパティやメソッドの使い方が簡単になります。  たとえば、上のオーバーロードされた `Display` メソッドを呼び出すには、以下のどのコード行でも使用できます。  
  
 [!code-vb[VbVbalrOOP#66](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#66)]  
  
 実行時には、指定したパラメーターのデータ型に基づき、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によって正しいプロシージャが呼び出されます。  
  
## オーバーロードの規則  
 オーバーロードされたクラスのメンバーを作成するには、同じ名前を持つ複数のプロパティまたはメソッドを追加します。  オーバーロードされた派生メンバーを除き、オーバーロードされた各メンバーは、それぞれパラメーター リストが異なっている必要があります。また、プロパティやプロシージャをオーバーロードするときには、以下の項目でそれぞれを区別することはできません。  
  
-   メンバーに適用される `ByVal` や `ByRef` などの修飾子、またはメンバーのパラメーター  
  
-   パラメーターの名前  
  
-   プロシージャの戻り値の型  
  
 オーバーロードを行うときに `Overloads` キーワードは省略可能ですが、オーバーロードされるメンバーのいずれかで `Overloads` キーワードを使用する場合には、同じ名前を持つ他のすべてのオーバーロードされるメンバーにもこのキーワードを指定する必要があります。  
  
 派生クラスは、継承したメンバーを同じパラメーター \(および同じパラメーター型\) を持つメンバーでオーバーロードできます。これは*名前とシグネチャによるシャドウ*と呼ばれます。  名前とシグネチャによるシャドウで `Overloads` キーワードを使用した場合は、基本クラス内の実装の代わりにメンバーの派生クラスの実装が使用され、そのメンバーに対する他のすべてのオーバーロードが派生クラスのインスタンスで使用できるようになります。  
  
 継承したメンバーを同じパラメーター \(および同じパラメーター型\) を持つメンバーでオーバーロードするときに `Overloads` キーワードを省略した場合、そのオーバーロードは*名前によるシャドウ*と呼ばれます。  名前によるシャドウを行うと、メンバーの継承した実装が置き換わります。派生クラスのインスタンスとその子孫は、他のすべてのオーバーロードを使用できなくなります。  
  
 `Overloads` 修飾子と `Shadows` 修飾子の両方を同じプロパティまたはメソッドで使用することはできません。  
  
### 例  
 次の例で作成するオーバーロードされたメソッドは、金額を `String` または `Decimal` の値として受け取って、消費税を加えた額を文字列として返します。  
  
##### この例を使ってオーバーロードされたメソッドを作成するには  
  
1.  新しいプロジェクトを開き、`TaxClass` という名前のクラスを追加します。  
  
2.  `TaxClass` クラスに次のコードを追加します。  
  
     [!code-vb[VbVbalrOOP#67](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#67)]  
  
3.  フォームに次のプロシージャを追加します。  
  
     [!code-vb[VbVbalrOOP#68](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#68)]  
  
4.  フォームにボタンを追加し、ボタンの `Button1_Click` イベントから `ShowTax` プロシージャを呼び出します。  
  
5.  プロジェクトを実行し、フォームのボタンをクリックして、オーバーロードされた `ShowTax` プロシージャをテストします。  
  
 実行時には、使用されているパラメーターに対応する適切な関数がコンパイラによって選択されます。  ボタンをクリックすると、オーバーロードされたメソッドがまず文字列の `Price` パラメーターで呼び出され、"Price is a String.  Tax is $5.12" というメッセージが表示されます。  次に、`Decimal` 値と共に `TaxAmount` が呼び出され、"Price is a Decimal.  Tax is $5.12" というメッセージが表示されます。  
  
## 参照  
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)   
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)   
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)