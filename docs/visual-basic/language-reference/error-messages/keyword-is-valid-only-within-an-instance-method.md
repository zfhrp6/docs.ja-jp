---
title: '&#39;です。&lt;キーワード&gt;&#39; は、インスタンス メソッド内でのみ有効です'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a61314c036cec0fd1412a9c844a610fbd1401add
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a>&#39;です。&lt;キーワード&gt;&#39; は、インスタンス メソッド内でのみ有効です
`Me`、 `MyClass`、および`MyBase`キーワードは、特定のクラスのインスタンスを参照してください。 共有内には使用できません`Function`または`Sub`プロシージャです。  
  
 **エラー ID:** BC30043  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   プロシージャからキーワードを削除するか、削除、`Shared`プロシージャ宣言からキーワード。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト変数の代入](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Me、My、MyBase、および MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
