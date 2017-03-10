---
title: "Me, My, MyBase, and MyClass in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "MyClass"
  - "vb.Me"
  - "MyBase"
  - "vb.MyBase"
  - "Me"
  - "vb.MyClass"
  - "vb.This"
  - "vb.My"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My object"
  - "self-reference, Me keyword"
  - "MyClass keyword, relationship to similar programming elements"
  - "Me keyword, relationship to similar programming elements"
  - "Me keyword, referring to the current instance of an object"
  - "Me keyword"
  - "self-reference"
  - "current instance, Me keyword"
  - "MyBase keyword, relationship to similar programming elements"
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Me, My, MyBase, and MyClass in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の `Me`、`My`、`MyBase`、および `MyClass` は名前は似ていますが、用途はそれぞれ異なります。  ここでは、これらの概念の違いを明確にするために、それぞれの特徴について説明します。  
  
## Me  
 `Me` キーワードを使用すると、コードが実行されているクラスまたは構造体の特定のインスタンスを参照できます。  `Me` は、現在のインスタンスを参照するオブジェクト変数または構造体変数のように動作します。  特に、別のクラス、構造体、またはモジュールのプロシージャに、クラスや構造体の現在のインスタンスに関する情報を渡す場合などには、`Me` が役立ちます。  
  
 たとえば、モジュール内に次のプロシージャがあったとします。  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 この場合に次のステートメントを使うと、上のプロシージャを呼び出し、<xref:System.Windows.Forms.Form> クラスの現在のインスタンスを引数として渡すことができます。  
  
```  
ChangeFormColor(Me)  
```  
  
## 担当  
 `My` は、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] の数多くのクラスに簡単かつ直観的にアクセスするための手段であり、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ユーザーがコンピューター、アプリケーション、設定、リソースなどとやり取りできるようにします。  
  
## MyBase  
 `MyBase` キーワードは、クラスの現在のインスタンスの基本クラスを参照するオブジェクト変数のように動作します。  `MyBase` は、派生クラスでオーバーライドまたはシャドウされている基本クラスのメンバーにアクセスする目的でよく使用されます。  `MyBase.New` は、派生クラスのコンストラクターから基本クラスのコンストラクターを明示的に呼び出すときに使用されます。  
  
## MyClass  
 `MyClass` キーワードは、クラスの現在のインスタンスを元の実装に従って参照するオブジェクト変数のように動作します。  `MyClass` は `Me` と似ていますが、MyClass で呼び出されるメソッドは、すべて `NotOverridable` であるかのように扱われます。  
  
## 参照  
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)