---
title: "XAML における xml:space の処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a5048cbad1d2ea914d041ac3c87a43223b208c3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xmlspace-handling-in-xaml"></a>XAML における xml:space の処理
`xml:space`属性はオブジェクト要素内で重要な空白の処理の動作を宣言する XML 定義の属性です。 この動作は、要素内に含まれるすべてのコンテンツ (内部テキ スト) に関連する場所`xml:space`が宣言されているし、もスコープの子要素にします。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- または  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>コメント  
 定義、`xml:space`からその 2 つの値を含む XAML の属性が派生した`xml:space`for XML の W3C 仕様で「特別な属性」として定義されています。  
  
 既定値、`xml:space`属性は、リテラル値`"default"`です。 値の`"default"`、または`xml:space`が反映されていません、すべてのトピックで定義されているの重要なホワイト スペースの解析中の動作は、既定の処理[XAML での空白の処理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)です。  
  
 オブジェクトの要素コンテンツ内の空白を保持するために指定`xml:space="preserve"`に、そのオブジェクト。  
  
 ほとんどの解釈、`xml:space`のスコープの子要素には属性の効果と属性の値。  
  
 空白の XAML の処理の詳細については、次を参照してください。 [XAML での空白の処理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)です。  
  
## <a name="see-also"></a>関連項目  
 [XAML での空白の処理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [XAML の概要 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
