---
title: 既定のプロパティ&#39; &lt;propertyname1&gt; &#39;既定のプロパティと競合しています&#39; &lt;propertyname2&gt; &#39;で&#39; &lt;classname&gt; &#39;ため、宣言する必要があります&#39;シャドウ&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: b305f7a59a9865ebeb6b6f53607757b719fb4d41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586625"
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>既定のプロパティ&#39; &lt;propertyname1&gt; &#39;既定のプロパティと競合しています&#39; &lt;propertyname2&gt; &#39;で&#39; &lt;classname&gt; &#39;ため、宣言する必要があります&#39;シャドウ&#39;
プロパティは、基本クラスで定義されたプロパティと同じ名前で宣言されます。 このような状況は、このクラスのプロパティは、基底クラスのプロパティをシャドウする必要があります。  
  
 このメッセージは警告です。 `Shadows` は、既定で指定されていると見なされます。 警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。  
  
 **エラー ID:** BC40007  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   追加、`Shadows`プロパティの名前が宣言されているキーワードを宣言、または変更します。  
  
## <a name="see-also"></a>関連項目  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
