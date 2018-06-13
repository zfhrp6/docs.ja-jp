---
title: '方法 : バインディングの検証の実装'
ms.date: 03/30/2017
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 347e38ba036e5c1a716a9edb75572c1a49f99631
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556966"
---
# <a name="how-to-implement-binding-validation"></a>方法 : バインディングの検証の実装
この例を使用する方法を示しています、<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>に無効な値が入力されると、ユーザーに通知する視覚的なフィードバックを提供するスタイルのトリガーのカスタム検証規則に基づいてとします。  
  
## <a name="example"></a>例  
 コンテンツのテキスト、<xref:System.Windows.Controls.TextBox>に次の例では、バインド、`Age`プロパティ (int 型) という名前のバインド ソース オブジェクトの`ods`します。 バインディングは、`AgeRangeRule` という名前の検証規則を使用するよう設定されているため、ユーザーが数字以外の文字、または 21 から 130 の範囲外の値を入力すると、テキスト ボックスの横に赤の感嘆符が表示され、ユーザーがテキスト ボックス上にマウスを置くとエラー メッセージを含んだツール ヒントが示されます。  
  
 [!code-xaml[BindValidation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 次の例は、の実装を示しています。 `AgeRangeRule`、から継承される<xref:System.Windows.Controls.ValidationRule>し、上書き、<xref:System.Windows.Controls.ValidationRule.Validate%2A>メソッドです。 Int32.Parse() メソッドは、値に無効な文字が含まれていないことを確認するために、値に対して呼び出されます。 <xref:System.Windows.Controls.ValidationRule.Validate%2A>メソッドを返します、<xref:System.Windows.Controls.ValidationResult>かどうか、値が有効では、解析中に例外をキャッチするかどうかと、下限と上限の外部では、有効期間の値かどうかに基づいていることを示します。  
  
 [!code-csharp[BindValidation#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 次の例は、カスタム<xref:System.Windows.Controls.ControlTemplate>`validationTemplate`赤色の感嘆符は、検証エラーをユーザーに通知を作成します。 コントロール テンプレートは、コントロールの外観を再定義するために使用されます。  
  
 [!code-xaml[BindValidation#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 次の例のように、<xref:System.Windows.Controls.ToolTip>という名前のスタイルを使用して、エラー メッセージの作成を示す`textBoxInError`です。 場合の値<xref:System.Windows.Controls.Validation.HasError%2A>は`true`、トリガーは、現在のツール ヒントを設定<xref:System.Windows.Controls.TextBox>をその最初の検証エラー。 <xref:System.Windows.Data.Binding.RelativeSource%2A>に設定されている<xref:System.Windows.Data.RelativeSourceMode.Self>の現在の要素を参照します。  
  
 [!code-xaml[BindValidation#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 コード例全体については、「[バインディングの検証のサンプル](http://go.microsoft.com/fwlink/?LinkID=159972)」をご覧ください。  
  
 カスタムを指定しない場合は、<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>検証エラーがある場合に、ユーザーに視覚的なフィードバックを提供する既定のエラー テンプレートが表示されます。 詳しくは、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」の「データの検証」をご覧ください。 さらに [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、バインディング ソース プロパティの更新中にスローされる例外をキャッチするための、組み込みの検証規則を提供します。 詳細については、「<xref:System.Windows.Controls.ExceptionValidationRule>」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
