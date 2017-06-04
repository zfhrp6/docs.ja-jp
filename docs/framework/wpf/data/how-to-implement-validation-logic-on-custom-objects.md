---
title: "方法 : カスタム オブジェクトに検証ロジックを実装する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "チェック (検証エラーを) [WPF]"
  - "カスタム オブジェクト [WPF], 実装 (検証ロジックを)"
  - "実装 (カスタム オブジェクトに検証ロジックを) [WPF]"
  - "検証エラー [WPF], チェック"
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : カスタム オブジェクトに検証ロジックを実装する
次のコード例は、カスタム オブジェクトに検証ロジックを実装してバインドする方法を示しています。  
  
## 使用例  
 次の例に示すように、ソース オブジェクトで <xref:System.ComponentModel.IDataErrorInfo> を実装する場合は、ビジネス層に検証ロジックを実装できます。  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 次の例では、テキスト ボックスのテキスト プロパティが `Person` オブジェクトの `Age` プロパティにバインドされています。このプロパティは、`x:Key` `data` が指定されたリソース宣言によってバインディング可能になっています。  <xref:System.Windows.Controls.DataErrorValidationRule> は、<xref:System.ComponentModel.IDataErrorInfo> の実装によって発生した検証エラーをチェックします。  
  
 [!code-xml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml#boundtextbox)]  
  
 また、<xref:System.Windows.Controls.DataErrorValidationRule> を使用する代わりに、<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> プロパティを `true` に設定する方法もあります。  
  
## 参照  
 <xref:System.Windows.Controls.ExceptionValidationRule>   
 [バインディングの検証の実装](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)