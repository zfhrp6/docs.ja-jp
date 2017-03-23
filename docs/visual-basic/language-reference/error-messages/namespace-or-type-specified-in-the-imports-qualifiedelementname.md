---
title: "Namespace or type specified in the Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc40056"
  - "vbc40056"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40056"
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Namespace or type specified in the Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

インポート '\<qualifiedelementname\>' で指定された名前空間または型が、パブリック メンバーを含んでいないか、または見つかりません。名前空間または型が定義されていて、少なくとも 1 つのパブリック メンバーを含んでいることを確認してください。エイリアスが他のエイリアスを含まないようにしてください。  
  
 `Imports` ステートメントが、コンテナー要素を指定していますが、それが見つからないか、`Public` メンバーを定義していません。  
  
 *コンテナー要素*は、名前空間、クラス、構造体、モジュール、インターフェイス、または列挙体です。  コンテナー要素には、変数、プロシージャ、その他のコンテナー要素などのメンバーが含まれます。  
  
 インポートの目的は、コードで名前空間または型のメンバーに修飾なしでアクセスできるようにすることです。  場合によっては、プロジェクトでも、名前空間または型への参照を追加することが必要になります。  詳細については、「[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」の「コンテナー要素のインポート」を参照してください。  
  
 指定されたコンテナー要素が見つからない場合、コンパイラはそれを使用する参照を解決できません。  要素が見つかっても、それが `Public` メンバーを一切公開しない場合、参照は成功しません。  どちらの場合も、要素をインポートしても無意味です。  
  
 コンテナー要素をインポートしてそれにインポート エイリアスを割り当てる場合は、そのインポート エイリアスを別の要素のインポートには使用できないことに注意してください。  次のコードはコンパイル エラーになります。  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **Error ID:** BC40056  
  
### このエラーを解決するには  
  
1.  プロジェクトからコンテナー要素にアクセスできることを確認します。  
  
2.  コンテナー要素の指定に、別のインポートのインポート エイリアスが含まれていないことを確認します。  
  
3.  コンテナー要素が少なくとも 1 つの `Public` メンバーを公開することを確認します。  
  
## 参照  
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)