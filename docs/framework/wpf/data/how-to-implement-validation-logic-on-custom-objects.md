---
title: "方法 : カスタム オブジェクトに検証ロジックを実装する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5044339e1d06bddad05151b2db99d5f96d068e77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a>方法 : カスタム オブジェクトに検証ロジックを実装する
この例では、カスタム オブジェクトに検証ロジックを実装し、それにバインドする方法を示します。  
  
## <a name="example"></a>例  
 ソース オブジェクトを実装する場合、ビジネス層の検証ロジックを指定できます<xref:System.ComponentModel.IDataErrorInfo>、次の例のようにします。  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 次の例では、テキスト ボックスのテキスト プロパティにバインドされて、`Age`のプロパティ、`Person`されていますが指定されたリソース宣言を通じてバインディングの使用可能なオブジェクト、`x:Key``data`です。 <xref:System.Windows.Controls.DataErrorValidationRule>によって発生した検証エラーのチェック、<xref:System.ComponentModel.IDataErrorInfo>実装します。  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml#boundtextbox)]  
  
 使用する代わりに、代わりに、 <xref:System.Windows.Controls.DataErrorValidationRule>、設定することができます、<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>プロパティを`true`です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.ExceptionValidationRule>  
 [バインディングの検証の実装](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
