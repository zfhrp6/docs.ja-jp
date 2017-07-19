---
title: "方法 : バインディングの検証の実装 | Microsoft Docs"
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
  - "バインド, 検証"
  - "データ バインディング, 検証 (バインディングの)"
  - "検証 (バインディングの)"
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : バインディングの検証の実装
この例では、<xref:System.Windows.Controls.Validation.ErrorTemplate%2A> およびスタイル トリガーを使用して、カスタム検証規則に基づき無効な値が入力されたことをユーザーに通知するための視覚的フィードバックを提供する方法を示します。  
  
## 使用例  
 次の例で使用されている <xref:System.Windows.Controls.TextBox> のテキスト コンテンツは、`ods` という名前の[バインディング ソース](GTMT) オブジェクトの `Age` プロパティ \(int 型\) にバインドされています。  バインドは、`AgeRangeRule` という名前の入力規則を使用するよう設定されています。つまり、ユーザーが数字以外の文字、または 21 ～ 130 の範囲外の数値を入力すると、テキスト ボックスの横に赤の感嘆符が表示され、ユーザーがテキスト ボックス上にマウスを置くとエラー メッセージを含んだツール ヒントが示されます。  
  
 [!code-xml[BindValidation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 次の例では `AgeRangeRule` の実装方法を示します。この規則は、<xref:System.Windows.Controls.ValidationRule> から継承され、<xref:System.Windows.Controls.ValidationRule.Validate%2A> メソッドをオーバーライドします。  Int32.Parse\(\) メソッドは、値に無効な文字が含まれていないことを確認するために、値に対して呼び出されます。  <xref:System.Windows.Controls.ValidationRule.Validate%2A> メソッドは、解析中に例外が発生したかどうか、および年齢値が範囲外にあるかどうかに基づいて、値が有効かどうかを示す <xref:System.Windows.Controls.ValidationResult> を返します。  
  
 [!code-csharp[BindValidation#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 次の例では、検証エラーをユーザーに通知する赤い感嘆符を作成するための、カスタム <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` を示します。  コントロール テンプレートは、コントロールの外観を再定義するために使用されます。  
  
 [!code-xml[BindValidation#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 次の例に示すように、エラー メッセージを表示する <xref:System.Windows.Controls.ToolTip> は、`textBoxInError` という名前のスタイル トリガーを使って作成されます。  <xref:System.Windows.Controls.Validation.HasError%2A> の値が `true` である場合、トリガーは現在の <xref:System.Windows.Controls.TextBox> のツール ヒントに、最初の検証エラーを設定します。  <xref:System.Windows.Data.Binding.RelativeSource%2A> には、現在の要素を参照している <xref:System.Windows.Data.RelativeSourceMode> が設定されます。  
  
 [!code-xml[BindValidation#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 コード例全体については、[バインディングの検証のサンプル](http://go.microsoft.com/fwlink/?LinkID=159972)を参照してください。  
  
 カスタム <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> を提供しない場合、検証エラーがあった際にユーザーに視覚的にフィードバックするために、既定のエラー テンプレートが使用されることに注意してください。  詳細については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」の「データの検証」を参照してください。  さらに [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、バインド ソース プロパティの更新中にスローされる例外をキャッチするための、組み込みの検証規則を提供します。  詳細については、「<xref:System.Windows.Controls.ExceptionValidationRule>」を参照してください。  
  
## 参照  
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)