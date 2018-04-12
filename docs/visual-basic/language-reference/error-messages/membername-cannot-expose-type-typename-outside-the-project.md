---
title: '&#39;です。&lt;membername&gt;&#39; の種類 &#39; に公開できません&lt;。typename&gt;&#39; 経由でプロジェクトの外部&lt;コンテナー&gt; &#39;&lt;containertypename&gt;&#39;です。'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd64c815286a5ffec111bcf1f68674a8e3558403
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>&#39;です。&lt;membername&gt;&#39; の種類 &#39; に公開できません&lt;。typename&gt;&#39; 経由でプロジェクトの外部&lt;コンテナー&gt; &#39;&lt;containertypename&gt;&#39;です。
変数、プロシージャのパラメーター、または関数の戻り値は、そのコンテナーでは、外部に公開されるが、コンテナーの外部公開してはならないを型として宣言されています。  
  
 次のスケルトン コードは、このエラーが発生する状況を示しています。  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 宣言されている型`Protected`、 `Friend`、 `Protected Friend`、または`Private`宣言コンテキストの外部アクセスを制限するためのものでは、します。 データとして使用する制限の少ない方のアクセス権を持つ変数の型に反しますこの目的。 上記のスケルトン コード`exposedVar`は`Public`公開と`privateClass`へのアクセス権のないコードにします。  
  
 **エラー ID:** BC30909  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   変数、プロシージャのパラメーター、または関数のアクセス レベルの変更は、少なくとも最小限にそのデータ型のアクセス レベルに戻ります。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
