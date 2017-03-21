---
title: "プロジェクト レベルのインポートで指定された Namespace または型&lt;qualifiedelementname&gt;&quot; すべてのパブリック メンバーが含まれていないか、見つけることはできません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40057
- bc40057
dev_langs:
- VB
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5dae6f92f573a57d0974c860500bc7420f55a94f
ms.lasthandoff: 03/13/2017

---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>プロジェクト レベルのインポートで指定された Namespace または型&lt;qualifiedelementname&gt;' すべてのパブリック メンバーが含まれていないか、見つけることはできません
プロジェクト レベルのインポートで指定された Namespace または型\<qualifiedelementname >' すべてのパブリック メンバーが含まれていないか、見つけることはできません。 名前空間または型が定義され、少なくとも&1; つのパブリック メンバーを含むことを確認します。 エイリアス名には、他のエイリアスにはが含まれていないことを確認します。  
  
 見つからない、またはいずれかが定義されていませんのあるコンテナーの要素を指定して、プロジェクトのインポート プロパティ`Public`メンバーです。  
  
 A*要素を含む*名前空間、クラス、構造体、モジュール、インターフェイス、または列挙型にすることができます。 コンテナー要素には、変数、プロシージャ、または他のコンテナー要素などのメンバーが含まれています。  
  
 インポートの目的は、修飾しなくても、コードを名前空間または型のメンバーへのアクセスを許可するようにです。 プロジェクトは、名前空間または型への参照を追加する必要もあります。 詳細については、「を含む要素のインポート」を参照してください[宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)します。  
  
 コンパイラでは、指定されたコンテナー要素を見つけられない場合、それを使用して参照を解決できません。 要素はいずれかを公開しませんが、要素が見つかった`Public`メンバー、参照が成功することができます。 いずれの場合は、要素をインポートしても意味です。  
  
 使用する、**プロジェクト デザイナー**をインポートする要素を指定します。 使用して、**インポートされた名前空間**のセクションで、**参照**ページです。 表示する、**プロジェクト デザイナー**をダブルクリックして、 **My Project**アイコン**ソリューション エクスプ ローラー**します。  
  
 **エラー ID:** BC40057  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  開いている、**プロジェクト デザイナー**に切り替えると、**参照**ページです。  
  
2.  **インポートされた名前空間**セクションで、コンテナーの要素が、プロジェクトからアクセス可能であることを確認します。  
  
3.  コンテナーの要素が少なくとも&1; つを公開することを確認`Public`メンバーです。  
  
## <a name="see-also"></a>関連項目  
 [[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)   
 [NIB 方法: プロジェクトのプロパティと構成設定の変更](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [パブリック](../../../visual-basic/language-reference/modifiers/public.md)   
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
