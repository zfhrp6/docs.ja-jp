---
title: "How to: Control the Availability of a Variable (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "access levels, declared elements"
  - "Private keyword, accessing variables"
  - "access levels, variables"
  - "Public keyword, accessing variables"
  - "Friend keyword, accessing variables"
  - "variables [Visual Basic], access level"
  - "declared elements, access level"
  - "Protected keyword, accessing variables"
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Control the Availability of a Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

変数の*アクセス レベル*を指定して、可用性を制御します。  アクセス レベルによって、どのコードが、変数の読み取りまたは書き込みのアクセス許可を持っているかが決まります。  
  
-   \(モジュール レベルおよびプロシージャの外部で定義される\) *メンバー変数*は、既定値であるパブリック アクセスに設定されます。つまり、メンバー変数を参照できるすべてのコードが、メンバー変数にアクセスできます。  アクセス修飾子を指定すると、これを変更できます。  
  
-   \(プロシージャの内部で定義される\) *ローカル変数*は、名目上パブリック アクセスを持っていますが、プロシージャ内のコードのみがローカル変数にアクセスできます。  ローカル変数のアクセス レベルは変更できませんが、ローカル変数が含まれるプロシージャのアクセス レベルは変更できます。  
  
 詳細については、「[Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
## プライベート アクセスおよびパブリック アクセス  
  
#### モジュール、クラス、または構造体内からだけ変数にアクセスできるようにするには  
  
1.  変数の [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) を、プロシージャの外部ではなく、モジュール、クラス、または構造体の内部に配置します。  
  
2.  `Dim` ステートメントには [Private](../../../../visual-basic/language-reference/modifiers/private.md) キーワードを含めます。  
  
     モジュール、クラス、または構造体内から変数の読み取りまたは書き込みを行うことができますが、外部からはできません。  
  
#### 変数を参照できるすべてのコードが、変数にアクセスできるようにするは  
  
1.  メンバー変数に対して、変数の `Dim` ステートメントを、プロシージャの外部ではなく、モジュール、クラス、または構造体の内部に配置します。  
  
2.  `Dim` ステートメントには [Public](../../../../visual-basic/language-reference/modifiers/public.md) キーワードを含めます。  
  
     アセンブリと相互運用しているどのコードからでも、変数の読み取りまたは書き込みを行うことができます。  
  
 または  
  
1.  ローカル変数に対して、変数の `Dim` ステートメントをプロシージャ内部に配置します。  
  
2.  `Dim` ステートメントには `Public` キーワードを含めないようにしてください。  
  
     プロシージャ内から変数の読み取りまたは書き込みを行うことができますが、外部からはできません。  
  
## Protected アクセスおよび Friend アクセス  
 変数のアクセス レベルを、クラスおよび派生クラス、またはアセンブリに制限できます。  また、これらの制限の共用体を指定して、派生クラスまたは同じアセンブリ内の他の場所にあるコードからのアクセスを可能にすることもできます。  同じ宣言内の `Protected` キーワードと `Friend` キーワードを組み合わせて、この共用体を指定します。  
  
#### クラスおよび派生クラスからだけ変数にアクセスできるようにするには  
  
1.  変数の `Dim` ステートメントを、プロシージャの外部ではなく、クラスの内部に配置します。  
  
2.  `Dim` ステートメントには [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) キーワードを含めます。  
  
     クラス内および派生したクラスのどの場所からでも、変数の読み取りまたは書き込みを行うことができますが、派生チェーンのクラスの外部からはできません。  
  
#### 同じアセンブリ内からだけ変数にアクセスできるようにするには  
  
1.  変数の `Dim` ステートメントを、プロシージャの外部ではなく、モジュール、クラス、または構造体の内部に配置します。  
  
2.  `Dim` ステートメントには [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) キーワードを含めます。  
  
     モジュール、クラス、または構造体内のすべての場所、および同じアセンブリ内のどのコードからでも、変数の読み取りまたは書き込みを行うことができますが、アセンブリの外部からはできません。  
  
## 使用例  
 `Public`、`Protected`、`Friend`、`Protected Friend`、および `Private` アクセス レベルを使用して、変数を宣言する例を示します。  `Dim` ステートメントによってアクセス レベルが指定される場合、`Dim` キーワードを含める必要はありません。  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## .NET Framework セキュリティ  
 変数のアクセス レベルが制限されるほど、悪意のあるコードによって不正使用される機会が少なくなります。  
  
## 参照  
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Public](../../../../visual-basic/language-reference/modifiers/public.md)   
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)   
 [Private](../../../../visual-basic/language-reference/modifiers/private.md)