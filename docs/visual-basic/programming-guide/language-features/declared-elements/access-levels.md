---
title: "Access Levels in Visual Basic | Microsoft Docs"
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
  - "members, accessing in Visual Basic"
  - "Friend access modifier"
  - "access levels, declared elements"
  - "access levels"
  - "access modifiers"
  - "Public access modifier"
  - "Protected access modifier"
  - "Protected Friend access modifier"
  - "Private access modifier"
  - "declared elements, access level"
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Access Levels in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

宣言された要素の*アクセス レベル*とは、その要素にアクセスするために必要な権限の程度、つまり、その要素に対する読み取りと書き込みの許可がどのようなコードに与えられるかを示します。  アクセス レベルは、要素自体を宣言する方法だけでなく、要素のコンテナーのアクセス レベルによっても左右されます。  コンテナー要素にアクセスできないコードは、そのコンテナー要素に含まれる要素にも一切アクセスできません。含まれる要素が `Public` として宣言されていても同じです。  たとえば、`Private` 構造体の中の `Public` 変数は、その構造体を含むクラス内からはアクセスできますが、そのクラスの外からはアクセスできません。  
  
## Public  
 宣言ステートメントで [Public](../../../../visual-basic/language-reference/modifiers/public.md) キーワードを使用して宣言した要素は、同じプロジェクト内からも、そのプロジェクトを参照している他のプロジェクトからも、そのプロジェクトからビルドされたアセンブリからもアクセスできます。  `Public` 宣言の例を次に示します。  
  
```  
Public Class classForEverybody  
```  
  
 `Public` は、モジュール レベル、インターフェイス レベル、または名前空間レベルでのみ使用できます。  つまり、パブリック要素は、ソース ファイルまたは名前空間のレベルか、インターフェイス内、モジュール内、クラス内、または構造体内では宣言できますが、プロシージャ内では宣言できません。  
  
## Protected  
 宣言ステートメントで [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) キーワードを使用して宣言した要素は、同じクラス、またはそのクラスの派生クラスからしかアクセスできません。  `Protected` 宣言の例を次に示します。  
  
```  
Protected Class classForMyHeirs  
```  
  
 `Protected` は、クラス レベルでのみ、しかも、クラスのメンバーを宣言する場合にのみ使用できます。  つまり、プロテクト要素は、クラス内では宣言できますが、ソース ファイルや名前空間のレベルと、インターフェイス内、モジュール内、構造体内、およびプロシージャ内では宣言できません。  
  
## Friend  
 宣言ステートメントで [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) キーワードを使用して宣言した要素は、同じアセンブリからはアクセスできますが、そのアセンブリの外部からはアクセスできません。  `Friend` 宣言の例を次に示します。  
  
```  
Friend stringForThisProject As String  
```  
  
 `Friend` は、モジュール レベル、インターフェイス レベル、または名前空間レベルでのみ使用できます。  つまり、フレンド要素は、ソース ファイルまたは名前空間のレベルか、インターフェイス内、モジュール内、クラス内、または構造体内では宣言できますが、プロシージャ内では宣言できません。  
  
## Protected Friend  
 宣言ステートメントで `Protected` キーワードと `Friend` キーワードの両方を使用して宣言した要素は、派生クラス内と同じアセンブリ内のいずれか、または両方からアクセスできます。  次のコードは、`Protected` `Friend` 宣言の例を示します。  
  
```  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 `Protected` `Friend` は、クラス レベルでのみ、しかも、クラスのメンバーを宣言する場合にのみ使用できます。  つまり、プロテクト フレンド要素は、クラス内では宣言できますが、ソース ファイルや名前空間のレベルと、インターフェイス内、モジュール内、構造体内、およびプロシージャ内では宣言できません。  
  
## Private  
 宣言ステートメントで [Private](../../../../visual-basic/language-reference/modifiers/private.md) キーワードを使用して宣言した要素は、同じモジュール、クラス、または構造体からしかアクセスできません。  `Private` 宣言の例を次に示します。  
  
```  
Private numberForMeOnly As Integer  
```  
  
 `Private` は、モジュール レベルでのみ使用できます。  つまり、プライベート要素は、モジュール内、クラス内、または構造体内では宣言できますが、ソース ファイルや名前空間のレベルと、インターフェイス内およびプロシージャ内では宣言できません。  
  
 モジュール レベルでは、アクセス レベル キーワードのない `Dim` ステートメントは、`Private` 宣言と等価です。  ただし、`Private` キーワードを使った方がコードがわかりやすくなります。  
  
## アクセス修飾子  
 アクセス レベルを指定するキーワードは、*アクセス修飾子*と呼ばれます。  アクセス修飾子の比較を次の表に示します。  
  
|\[アクセス修飾子\]|付与されるアクセス レベル|このアクセス レベルで宣言できる要素|この修飾子を使用できる宣言コンテキスト|  
|-----------------|-------------------|------------------------|-------------------------|  
|`Public`|無制限:<br /><br /> パブリック要素を参照できるすべてのコードがアクセスできます。|インターフェイス<br /><br /> モジュール<br /><br /> Classes<br /><br /> 構造体<br /><br /> 構造体メンバー<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙型<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|ソース ファイル<br /><br /> 名前空間<br /><br /> Interface<br /><br /> Module<br /><br /> Class<br /><br /> Structure|  
|`Protected`|派生:<br /><br /> プロテクト要素を宣言するクラス内のコード、またはそのクラスの派生したクラスが、この要素にアクセスできます。|インターフェイス<br /><br /> Classes<br /><br /> 構造体<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙型<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|Class|  
|`Friend`|アセンブリ:<br /><br /> フレンド要素が宣言されているアセンブリ内のコードが、この要素にアクセスできます。|インターフェイス<br /><br /> モジュール<br /><br /> Classes<br /><br /> 構造体<br /><br /> 構造体メンバー<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙型<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|ソース ファイル<br /><br /> 名前空間<br /><br /> Interface<br /><br /> Module<br /><br /> Class<br /><br /> Structure|  
|`Protected` `Friend`|`Protected` と `Friend` の結合:<br /><br /> プロテクト フレンド要素と同じクラスまたは同じアセンブリ内のコード、または要素のクラスから派生した各クラス内から、要素にアクセスできます。|インターフェイス<br /><br /> Classes<br /><br /> 構造体<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙型<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|Class|  
|`Private`|宣言コンテキスト:<br /><br /> 含まれている型の中のコードを含め、プライベート要素が宣言されている型内のコードが、要素にアクセスできます。|インターフェイス<br /><br /> Classes<br /><br /> 構造体<br /><br /> 構造体メンバー<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙型<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|Module<br /><br /> Class<br /><br /> Structure|  
  
## 参照  
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [How to: Control the Availability of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)   
 [Variables](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)