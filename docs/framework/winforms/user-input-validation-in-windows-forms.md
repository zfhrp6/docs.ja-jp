---
title: Windows フォームでのユーザー入力の検証
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: adc138ad1e277f69f27f9f86fc5c3ea28a8d5cce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541808"
---
# <a name="user-input-validation-in-windows-forms"></a>Windows フォームでのユーザー入力の検証
ユーザーがアプリケーションにデータを入力する場合、アプリケーションがそれを使用する前に、データが有効であることを確認します。 特定のテキスト フィールドにならないこと長さがゼロでフィールドが、電話番号などの適切な形式のデータの型として書式設定されること、または文字列がデータベースのセキュリティを侵害するために使用できる任意の安全でない文字を含まないことを要求することがあります。 Windows フォームでは、アプリケーションで入力を検証するためのいくつかの方法を提供します。  
  
## <a name="validation-with-the-maskedtextbox-control"></a>MaskedTextBox コントロールによる検証  
 ユーザーに電話番号または部品番号など、適切に定義された形式でデータを入力する必要がある場合は、これを行う迅速に、最小限のコードを使用して、<xref:System.Windows.Forms.MaskedTextBox>コントロール。 A*マスク*所定の位置でテキスト ボックスに入力できる文字を指定するマスク言語の文字から成る文字列です。 コントロールには、ユーザーに一連のプロンプトが表示されます。 ユーザーが間違って入力した場合、たとえば、1 桁の数字が必要な場合、文字を入力、コントロールは、入力を自動的に拒否します。  
  
 によって使用される、マスク言語<xref:System.Windows.Forms.MaskedTextBox>は非常に柔軟です。 必要となる文字、省略可能な文字、リテラル文字、ハイフン、かっこなど、通貨記号、および日付の区切り記号を指定できます。 コントロールも、データ ソースにバインドした場合でも機能します。 <xref:System.Windows.Forms.Binding.Format>のデータ バインディング イベントを使用して、マスクに準拠する受信データの書式を変更することができます、<xref:System.Windows.Forms.Binding.Parse>イベントを送信したデータ フィールドの仕様に準拠するデータを書式設定を使用できます。  
  
 詳細については、次を参照してください。 [MaskedTextBox コントロール](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)です。  
  
## <a name="event-driven-validation"></a>イベント ドリブンの検証  
 表示する場合、検証を完全にプログラムで制御や複雑な検証チェックを実行する必要があります、ほとんどの Windows フォーム コントロールに組み込まれている検証イベントを使用する必要があります。 各コントロールを自由にユーザー入力を受け付けるには、<xref:System.Windows.Forms.Control.Validating>コントロール データの検証に必要なときに発生するイベントです。 <xref:System.Windows.Forms.Control.Validating>イベント処理メソッドでは、ユーザーのいくつかの方法で入力を検証できます。 たとえば、郵便番号コードを含める必要があるテキスト ボックスがある場合は、次の方法で検証を実行できます。  
  
-   郵便番号は、郵便番号の特定のグループに属している必要がある場合、は、ユーザーが入力データを検証する入力文字列の比較を実行できます。 たとえば、郵便番号は、セット {10001、10002、10003} にする必要がある場合、は、データの検証に文字列比較を使用できます。  
  
-   特定の形式である必要があります、郵便番号場合は、ユーザーが入力データを検証する正規表現を使用できます。 たとえば、フォームを検証する`#####`または`#####-####`、正規表現を使用する`^(\d{5})(-\d{4})?$`です。 フォームを検証する`A#A #A#`、正規表現を使用する`[A-Z]\d[A-Z] \d[A-Z]\d`です。 正規表現の詳細については、次を参照してください。 [.NET Framework 正規表現](../../../docs/standard/base-types/regular-expressions.md)と[正規表現の例](../../../docs/standard/base-types/regular-expression-examples.md)です。  
  
-   郵便番号は、有効な米国の郵便である必要がある場合、は、ユーザーが入力データを検証する郵便番号 Web サービスを呼び出す可能性があります。  
  
 <xref:System.Windows.Forms.Control.Validating>イベントが指定された型のオブジェクト<xref:System.ComponentModel.CancelEventArgs>です。 取り消すことができますが、コントロールのデータが無効であると判断した場合、<xref:System.Windows.Forms.Control.Validating>するには、このオブジェクトのイベント<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>プロパティを`true`です。 設定しない場合、<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>プロパティ、Windows フォームは、そのコントロールが正常に検証するいると仮定させて、<xref:System.Windows.Forms.Control.Validated>イベント。  
  
 電子メール アドレスを検証するコード例については、<xref:System.Windows.Controls.TextBox>を参照してください<xref:System.Windows.Forms.Control.Validating>です。  
  
### <a name="data-binding-and-event-driven-validation"></a>データ バインディングとイベント ドリブンの検証  
 検証は、データベース テーブルなどのデータ ソースにコントロールがバインドされているときに非常に便利です。 確認することができます、検証を使用して、コントロールのデータがデータ ソースで必要な形式を満たす、そのことにはない引用符などの特殊文字を含めるとできない可能性がありますセーフであります。  
  
 実行中に、データ ソースとに、コントロール内のデータが同期されているデータ バインディングを使用するとき、<xref:System.Windows.Forms.Control.Validating>イベント。 キャンセルすると、<xref:System.Windows.Forms.Control.Validating>イベント、データは、データ ソースと同期されません。  
  
> [!IMPORTANT]
>  カスタム検証が行われたことがある場合、<xref:System.Windows.Forms.Control.Validating>イベントには、データ バインディングで影響しません。 コードがある場合など、<xref:System.Windows.Forms.Control.Validated>データ バインディングをキャンセルしようとするイベント、データ バインディングは行われます。 検証を実行するのには、この場合で、<xref:System.Windows.Forms.Control.Validated>イベント、管理の変更**データ ソース更新モード**プロパティ (**(Databindings) の下にある**\\ **(詳細)**) から**OnValidation**に**Never**、し、追加*コントロール*`.DataBindings["`*\<YOURFIELD >* `"].WriteValue()`検証コードにします。  
  
### <a name="implicit-and-explicit-validation"></a>暗黙的および明示的な検証  
 これはいつコントロールのデータ取得検証しますか。 これは、ユーザー、開発者の責任です。 アプリケーションのニーズに応じて、暗黙的または明示的な検証を使用することができます。  
  
#### <a name="implicit-validation"></a>暗黙の検証  
 暗黙的な検証方法は、ユーザーが入力するようにデータを検証します。 ユーザーが 1 つのコントロールから入力フォーカスを受け取るし、次に移動するたびに通常以上のようが押されたキーを読み取ることによってコントロールにデータを入力すると、データを検証することができます。 この方法は、作業しているように、データに関するユーザーの直接のフィードバックを付与するときに便利です。  
  
 コントロールの暗黙的な検証を使用する場合は、そのコントロールを設定する必要があります<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>プロパティを`true`です。 キャンセルすると、<xref:System.Windows.Forms.Control.Validating>イベント、コントロールの動作に割り当てられている値によって決定されます<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>です。 割り当てた場合<xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>、イベントをキャンセルすると、<xref:System.Windows.Forms.Control.Validated>イベントが発生するされません。 ユーザーは、有効な入力をデータを変更するまでは、入力フォーカスが現在のコントロール上に残ります。 割り当てた場合<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>、<xref:System.Windows.Forms.Control.Validated>イベントは、イベントをキャンセルするが、次のコントロールにフォーカスを移動も発生しません。  
  
 割り当てる<xref:System.Windows.Forms.AutoValidate.Disable>を<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>プロパティの暗黙的な検証はまったく行われません。 コントロールを検証するには、明示的な検証を使用する必要があります。  
  
#### <a name="explicit-validation"></a>明示的な検証  
 明示的な検証方法は、一度に 1 つのデータを検証します。 [保存] ボタンまたは [次へ] のリンクのクリックしてなどのユーザー アクションへの応答内のデータを検証することができます。 ユーザー アクションが発生したときに、明示的な検証をトリガーするには、次の方法のいずれか。  
  
-   呼び出す<xref:System.Windows.Forms.ContainerControl.Validate%2A>フォーカスが失われた最後のコントロールを検証します。  
  
-   呼び出す<xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A>フォームまたはコンテナー コントロール内のすべての子コントロールを検証します。  
  
-   コントロール内のデータを手動で検証するカスタム メソッドを呼び出します。  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>暗黙的な検証デフォルトでは、Windows フォーム コントロール  
 別の Windows フォーム コントロールごとに異なる既定があるその<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>プロパティです。 次の表は、最も一般的なコントロールとその既定値を示します。  
  
|コントロール|既定の検証動作|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Visual Studio で公開されていないプロパティ|  
|<xref:System.Windows.Forms.ToolStripContainer>|Visual Studio で公開されていないプロパティ|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>フォームを閉じると、検証のオーバーライド  
 コントロールが含まれているデータが正しくないために、フォーカスを管理しているときに、通常の方法のいずれかで、親フォームを閉じることはできません。  
  
-   クリックして、**閉じる**ボタンをクリックします。  
  
-   選択して**閉じる**で、**システム**メニュー。  
  
-   呼び出して、<xref:System.Windows.Forms.Form.Close%2A>メソッド プログラムでします。  
  
 ただし、場合によっては、ユーザーがコントロール内の値が有効かどうかに関係なく、フォームを閉じますできるようにする必要があります。 検証をオーバーライドして、フォームのハンドラーを作成することで無効なデータをまだ含まれているフォームを閉じます<xref:System.Windows.Forms.Form.Closing>イベント。 このイベントでは、設定、<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>プロパティを`false`です。 これにより、フォームを閉じます。 使用例を含む詳細については、「<xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>」を参照してください。  
  
> [!NOTE]
>  フォームを閉じるには、この方法を強制すると、既に保存されていないするフォームのコントロール内のデータは失われます。 さらに、モーダル フォームは、閉じられるときにコントロールの内容を検証しません。 コントロールにフォーカスをロックするコントロールの検証を使用することもできますが、フォームを閉じると関連付けられた動作について考慮する必要はありません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
 <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>  
 [MaskedTextBox コントロール](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)  
 [正規表現の例](../../../docs/standard/base-types/regular-expression-examples.md)
