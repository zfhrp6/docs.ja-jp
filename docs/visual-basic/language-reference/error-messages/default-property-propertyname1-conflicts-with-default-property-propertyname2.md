---
title: "既定のプロパティ &quot;&lt;propertyname1&gt;&quot;既定のプロパティは&quot;&lt;propertyname2&gt;&quot;で&quot;&lt;classname&gt;&quot;、&quot;Shadows&quot; と宣言する必要があります |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
dev_langs:
- VB
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 9
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
ms.openlocfilehash: 803b42b7659c16fd97251635e4b6ba49362e0a02
ms.lasthandoff: 03/13/2017

---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>既定のプロパティ '&lt;propertyname1&gt;'既定のプロパティは'&lt;propertyname2&gt;'で'&lt;classname&gt;'、'Shadows' と宣言する必要があります
プロパティは、基本クラスで定義されたプロパティと同じ名前の宣言します。 このような状況でこのクラスのプロパティは、基本クラスのプロパティをシャドウする必要があります。  
  
 このメッセージは警告です。 `Shadows`既定で見なされます。 警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。  
  
 **エラー ID:** BC40007  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   追加、`Shadows`プロパティの名前が宣言されるキーワードを宣言、または変更します。  
  
## <a name="see-also"></a>関連項目  
 [シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
