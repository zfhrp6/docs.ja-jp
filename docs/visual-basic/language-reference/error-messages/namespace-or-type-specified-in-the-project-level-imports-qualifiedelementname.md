---
title: "Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found | Microsoft Docs"
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
  - "vbc40057"
  - "bc40057"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40057"
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プロジェクト レベルのインポート '\<qualifiedelementname\>' で指定された名前空間または型が、パブリック メンバーを含んでいないか、または見つかりません。名前空間または型が定義されていて、少なくとも 1 つのパブリック メンバーを含んでいることを確認してください。エイリアスが他のエイリアスを含まないようにしてください。  
  
 プロジェクトのインポート プロパティが  コンテナー要素を指定していますが、それが見つからないか、`Public` メンバーが定義されていません。  
  
 *コンテナー要素*は、名前空間、クラス、構造体、モジュール、インターフェイス、または列挙体です。  コンテナー要素には、変数、プロシージャ、その他のコンテナー要素などのメンバーが含まれます。  
  
 インポートの目的は、コードで名前空間または型のメンバーに修飾なしでアクセスできるようにすることです。  場合によっては、プロジェクトでも、名前空間または型への参照を追加することが必要になります。  詳細については、「[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」の「コンテナー要素のインポート」を参照してください。  
  
 指定されたコンテナー要素が見つからない場合、コンパイラはそれを使用する参照を解決できません。  要素が見つかっても、それが `Public` メンバーを一切公開しない場合、参照は成功しません。  どちらの場合も、要素をインポートしても無意味です。  
  
 **プロジェクト デザイナー**を使用して、インポートする要素を指定します。  **\[参照設定\]** ページの **\[インポートされた名前空間\]** セクションを使用します。  **ソリューション エクスプローラー**の **\[My Project\]** アイコンをダブルクリックして、**プロジェクト デザイナー**に移動します。  
  
 **Error ID:** BC40057  
  
### このエラーを解決するには  
  
1.  **プロジェクト デザイナー**を開き、**\[参照\]** ページに切り替えます。  
  
2.  **\[インポートされた名前空間\]** セクションで、プロジェクトからコンテナー要素にアクセスできることを確認します。  
  
3.  コンテナー要素が少なくとも 1 つの `Public` メンバーを公開することを確認します。  
  
## 参照  
 [\[参照設定\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](../Topic/References%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)