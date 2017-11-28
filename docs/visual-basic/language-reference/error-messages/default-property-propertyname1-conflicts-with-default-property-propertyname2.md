---
title: "既定のプロパティ &#39;&lt;propertyname1&gt;&#39; 既定のプロパティ &#39; と競合しています&lt;propertyname2&gt;&#39; &#39;&lt;classname&gt;&#39; ため、宣言する必要があります (& a) #39 です。Shadows &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords: BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af92c06f6d07b6ea64a05b9043547a46e3679111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>既定のプロパティ &#39;&lt;propertyname1&gt;&#39; 既定のプロパティ &#39; と競合しています&lt;propertyname2&gt;&#39; &#39;&lt;classname&gt;&#39; ため、宣言する必要があります (& a) #39 です。Shadows &#39;
プロパティは、基本クラスで定義されたプロパティと同じ名前で宣言されます。 このような状況は、このクラスのプロパティは、基底クラスのプロパティをシャドウする必要があります。  
  
 このメッセージは警告です。 `Shadows` は、既定で指定されていると見なされます。 警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。  
  
 **エラー ID:** BC40007  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   追加、`Shadows`プロパティの名前が宣言されているキーワードを宣言、または変更します。  
  
## <a name="see-also"></a>関連項目  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
