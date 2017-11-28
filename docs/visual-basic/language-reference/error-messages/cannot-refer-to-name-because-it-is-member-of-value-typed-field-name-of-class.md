---
title: "参照できません &#39;です。&lt;名前&gt;&#39;以外の値に型指定されたフィールド &#39; のメンバーになっているため&lt;名前&gt;&#39; クラス &#39; の&lt;classname&gt;&#39; を持つ &#39;'System.marshalbyrefobject' &#39;基底クラスとして"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords: BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a84811b9f0e706cf3ebede09e07c03bd7e4cea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>参照できません &#39;です。&lt;名前&gt;&#39;以外の値に型指定されたフィールド &#39; のメンバーになっているため&lt;名前&gt;&#39; クラス &#39; の&lt;classname&gt;&#39; を持つ &#39;'System.marshalbyrefobject' &#39;基底クラスとして
`System.MarshalByRefObject`クラスには、アプリケーション ドメインの境界を越えてオブジェクトへのリモート アクセスをサポートするアプリケーションができるようにします。 型を継承する必要があります、`MarshalByRejectObject`クラスの種類をアプリケーション ドメインの境界を越えて使用するとします。 オブジェクトのメンバーが作成されたアプリケーション ドメインの外部で使用可能ではないために、オブジェクトの状態はコピーされません必要があります。  
  
 **エラー ID:** BC30310  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  参照されているメンバーは、有効かどうかを確認への参照を確認してください。  
  
2.  持つメンバーを明示的に修飾、`Me`キーワード。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.MarshalByRefObject>  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)
