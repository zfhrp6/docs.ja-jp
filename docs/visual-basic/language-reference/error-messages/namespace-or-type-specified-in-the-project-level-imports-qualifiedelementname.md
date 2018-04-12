---
title: Namespace またはプロジェクト レベルのインポート &#39; で指定された型&lt;qualifiedelementname&gt;&#39; しません &#39; t がすべてのパブリック メンバーを含めるか、または見つかりません
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d0a164562524af239b3b130f681dbc6eff23814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Namespace またはプロジェクト レベルのインポート &#39; で指定された型&lt;qualifiedelementname&gt;&#39; しません &#39; t がすべてのパブリック メンバーを含めるか、または見つかりません
プロジェクト レベル インポートで指定された Namespace または型\<qualifiedelementname >'、パブリック メンバーが含まれていないか、または見つかりません。 確認してください、名前空間または型が定義されている少なくとも 1 つのパブリック メンバーが含まれています。 エイリアス名には他のエイリアスが含まれていないことを確認してください。  
  
 見つからない、またはいずれかを一切定義しませんをコンテナー要素を指定して、プロジェクトのインポート プロパティ`Public`メンバー。  
  
 A*要素を含む*名前空間、クラス、構造体、モジュール、インターフェイス、または列挙型にすることができます。 コンテナー要素には、変数、プロシージャ、または他のコンテナー要素などのメンバーが含まれています。  
  
 インポートの目的は、それらを修飾することがなく、名前空間または型メンバーにアクセスするようにコードを許可します。 プロジェクトは、名前空間または型への参照を追加する必要もあります。 詳細については、「を含む要素をインポートする」を参照してください[宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)です。  
  
 コンパイラに指定されたコンテナーの要素が見つからない場合、それを使用する参照を解決できません。 かどうか、要素が見つかったが、要素はいずれかを公開しません`Public`メンバー、その参照はありませんが、成功することができます。 どちらの場合は意味が要素をインポートします。  
  
 使用する、**プロジェクト デザイナー**をインポートする要素を指定します。 使用して、**インポートされた名前空間**のセクションで、**参照**ページ。 取得する、**プロジェクト デザイナー**をダブルクリックして、 **My Project**アイコン**ソリューション エクスプ ローラー**です。  
  
 **エラー ID:** BC40057  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  開く、**プロジェクト デザイナー**に切り替えると、**参照**ページ。  
  
2.  **インポートされた名前空間**セクションで、コンテナーの要素が、プロジェクトからアクセスできることを確認します。  
  
3.  コンテナーの要素が少なくとも 1 つを公開することを確認`Public`メンバー。  
  
## <a name="see-also"></a>関連項目  
 [[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
