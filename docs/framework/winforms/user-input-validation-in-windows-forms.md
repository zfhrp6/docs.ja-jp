---
title: "Windows フォームでのユーザー入力の検証 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ユーザー入力, 検証 (Windows フォームで)"
  - "検証 (ユーザー入力の), Windows フォーム"
  - "検証, Windows フォームのユーザー入力"
  - "Windows フォーム, 検証 (ユーザー入力の)"
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Windows フォームでのユーザー入力の検証
ユーザーがアプリケーションにデータを入力する場合、アプリケーションがそのデータを使用する前に、データが有効であるかどうかの検証が必要になることがあります。  たとえば、テキスト フィールドの長さがゼロでないこと、フィールドの形式が電話番号や他の形式のデータとして適していること、または、文字列に、データベースのセキュリティに危険を与える可能性がある安全でない文字が含まれていないことを確認したりします。  Windows フォームは、アプリケーションでの入力を検証するさまざまな方法を提供します。  
  
## MaskedTextBox コントロールによる検証  
 電話番号や部品番号のように特定の形式でユーザーがデータを入力する必要がある場合は、<xref:System.Windows.Forms.MaskedTextBox> コントロールを使用することで、これを簡単に、かつ最小限のコードで実現できます。  *マスク*は、テキスト ボックス内の所定の位置に入力できる文字を指定する、マスキング言語の文字から成る文字列です。  コントロールは、ユーザーに対して一連のプロンプトを表示します。  数字が要求される場所に文字を入力しようとするなど、ユーザーが正しくないエントリを入力すると、コントロールは自動的に入力を拒否します。  
  
 <xref:System.Windows.Forms.MaskedTextBox> で使用されるマスク言語は非常に柔軟性があり、  必須文字、オプション文字、ハイフンやかっこなどのリテラル文字、通貨記号、および日付の区切り記号を指定できます。  コントロールは、データ ソースとバインドしている場合にも適切に動作します。  データ バインディングに対して <xref:System.Windows.Forms.Binding.Format> イベントを使用すると、受信データをマスクに合わせて再設定できます。<xref:System.Windows.Forms.Binding.Parse> イベントを使用すると、データ フィールドの指定に合わせて送信データを再設定できます。  
  
 詳細については、「[MaskedTextBox コントロール](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)」を参照してください。  
  
## イベント ドリブン検証  
 プログラムで検証を完全に制御する場合、または、複雑な検証チェックを実行する必要がある場合は、大部分の Windows フォーム コントロールに組み込まれている検証イベントを使用します。  自由形式のユーザー入力を受け取る各コントロールは <xref:System.Windows.Forms.Control.Validating> イベントを備えており、、コントロールがデータ検証を要求するとこのイベントが発生します。  <xref:System.Windows.Forms.Control.Validating> イベント処理メソッドを使用すると、ユーザーの入力をさまざまな方法で検証できます。  たとえば、郵便番号を入力するテキスト ボックスがある場合、次のような方法で検証を実行できます。  
  
-   そこに特定のグループに属する郵便番号を入力する必要がある場合、入力値に対して文字列比較を実行し、ユーザーの入力データを検証できます。  たとえば、{10001, 10002, 10003} という集合に含まれる郵便番号を入力する必要がある場合、文字列比較を使用してデータを検証できます。  
  
-   特定の形式で郵便番号を入力する必要がある場合は、正規表現を使用してユーザーの入力データを検証できます。  たとえば、`#####` または `#####-####` という形式を検証する場合、正規表現 `^(\d{5})(-\d{4})?$` を使用できます。  `A#A #A#` という形式を検証するには、正規表現 `[A-Z]\d[A-Z] \d[A-Z]\d` を使用できます。  正規表現の詳細については、「[.NET Framework の正規表現](../../../docs/standard/base-types/regular-expressions.md)」および「[正規表現の例](../../../docs/standard/base-types/regular-expression-examples.md)」を参照してください。  
  
-   有効なアメリカ合衆国郵便番号を入力する必要がある場合、郵便番号の Web サービスを呼び出して、ユーザーの入力データを検証することもできます。  
  
 <xref:System.Windows.Forms.Control.Validating> イベントには、<xref:System.ComponentModel.CancelEventArgs> 型のオブジェクトを提供します。  コントロールのデータが有効でないと判断した場合は、このオブジェクトの <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> プロパティを `true` に設定することによって、<xref:System.Windows.Forms.Control.Validating> イベントをキャンセルできます。  <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> プロパティが設定されない場合は、そのコントロールの検証が正常終了したものと見なされ、<xref:System.Windows.Forms.Control.Validated> イベントが発生します。  
  
 <xref:System.Windows.Controls.TextBox> で電子メール アドレスを検証するコード例については、<xref:System.Windows.Forms.Control.Validating> のトピックを参照してください。  
  
### データ バインディングおよびイベント ドリブン検証  
 コントロールがデータベース テーブルなどのデータ ソースにバインドされている場合、検証は非常に効果的です。  検証を使用すると、コントロールのデータがデータ ソースに適した形式であることや、安全でない可能性がある引用符やバック スラッシュなどの特殊文字を含まないことを確認できます。  
  
 データ バインディングを使用すると、コントロール内のデータは、<xref:System.Windows.Forms.Control.Validating> イベントの実行中、データ ソースと同期します。  <xref:System.Windows.Forms.Control.Validating> イベントをキャンセルすると、データはデータ ソースと同期しません。  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.Control.Validating> イベントの後に実行するカスタム検証の場合は、データ バインディングに影響しません。  たとえば、<xref:System.Windows.Forms.Control.Validated> イベント内にデータ バインディングをキャンセルするコードがある場合でも、データ バインディングは発生します。  この場合、<xref:System.Windows.Forms.Control.Validated> イベント内で検証を実行するには、コントロールの **\[データ ソース更新モード\]** プロパティ \(**\[\(Databindings\)\]**\\**\[\(詳細\)\]** の下\) を **\[OnValidation\]** から **\[Never\]** に変更し、検証コードに *Control*`.DataBindings["`*\<YOURFIELD\>*`"].WriteValue()` を追加します。  
  
### 暗黙の検証と明示的な検証  
 では、コントロールのデータはいつ検証を受けるのでしょうか。  その答えは、開発者しだいです。  アプリケーションの必要性に応じて、暗黙の検証と明示的な検証のいずれかを使用できます。  
  
#### 暗黙の検証  
 暗黙の検証は、ユーザーがデータを入力するたびに検証する方法です。  キーの押下を読み取って、コントロールに入力されるデータを検証することもできますが、さらに一般的な方法としては、ユーザーがあるコントロールから次へ入力フォーカスを移動したときにデータを検証できます。  この方法は、入力中のデータについて、ユーザーに対して直ちにフィードバックを返す場合に有効です。  
  
 あるコントロールに対する暗黙の検証を使用する場合、そのコントロールの <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> プロパティを `true` に設定します。  <xref:System.Windows.Forms.Control.Validating> イベントをキャンセルした場合、コントロールの動作は <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> に割り当てた値によって決定されます。  <xref:System.Windows.Forms.AutoValidate> を割り当てた場合は、イベントをキャンセルしても、<xref:System.Windows.Forms.Control.Validated> イベントが発生しません。  ユーザーが有効なデータを入力するまで、入力フォーカスは現在のコントロールから移動しません。  <xref:System.Windows.Forms.AutoValidate> を割り当てた場合は、イベントをキャンセルしても <xref:System.Windows.Forms.Control.Validated> イベントは発生せず、フォーカスはそのまま次のコントロールに移ります。  
  
 <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> プロパティに <xref:System.Windows.Forms.AutoValidate> を割り当てると、暗黙の検証がまったく行われません。  コントロールを検証するには、明示的な検証を使用する必要があります。  
  
#### 明示的な検証  
 明示的な検証は、データを 1 回で検証する方法です。  あるユーザー アクションが発生したとき \(\[保存\] ボタンや \[次へ\] リンクをクリックするなど\) に、データを検証することができます。  そのユーザー アクションが発生したときに明示的な検証をトリガーするには、次のいずれかを実行します。  
  
-   <xref:System.Windows.Forms.ContainerControl.Validate%2A> を呼び出して、最後のコントロールがフォーカスを失ったことを確認します。  
  
-   <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> を呼び出して、フォーム コントロールまたはコンテナー コントロールのすべての子コントロールを検証します。  
  
-   カスタム メソッドを呼び出して、コントロールのデータを手動で検証します。  
  
#### Windows フォーム コントロールにおける既定の暗黙の検証動作  
 Windows フォーム コントロールの <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> プロパティの既定値は、種類によってそれぞれ異なります。  最も一般的なコントロールとその既定値を次の表に示します。  
  
|Control|既定の検証動作|  
|-------------|-------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate>|  
|<xref:System.Windows.Forms.PropertyGrid>|Visual Studio の中でプロパティは公開されない|  
|<xref:System.Windows.Forms.ToolStripContainer>|Visual Studio の中でプロパティは公開されない|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate>|  
  
## フォームを閉じて検証をオーバーライドする  
 データが無効なためにフォーカスがコントロールに維持される場合、次のような通常の方法でフォームを閉じようとしても、親フォームを閉じることができません。  
  
-   **\[閉じる\]** をクリックする。  
  
-   **\[システム\]** メニューの **\[閉じる\]** をクリックする。  
  
-   プログラムで <xref:System.Windows.Forms.Form.Close%2A> メソッドを呼び出す。  
  
 ただし、場合によっては、コントロール内の値が有効かどうかにかかわらず、ユーザーがフォームを閉じることができるようにする必要があります。  フォームの <xref:System.Windows.Forms.Form.Closing> イベントのハンドラーを作成することにより、検証をオーバーライドして、無効なデータを含んでいるフォームを閉じることができます。  このイベント内で、<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> プロパティを `false` に設定します。  これにより、フォームが強制的に閉じられます。  詳細および使用例については、「<xref:System.Windows.Forms.Form.Closing?displayProperty=fullName>」を参照してください。  
  
> [!NOTE]
>  フォームをこのように強制的に閉じると、そのフォームのコントロール内の保存されていないデータはすべて失われます。  また、モーダル フォームは、閉じられるときにコントロールの内容を検証しません。  コントロールの検証を使用してフォーカスをコントロールにロックすることはできますが、フォームを閉じるときの動作を考慮する必要はありません。  
  
## 参照  
 <xref:System.Windows.Forms.Control.Validating?displayProperty=fullName>   
 <xref:System.Windows.Forms.Form.Closing?displayProperty=fullName>   
 <xref:System.ComponentModel.CancelEventArgs?displayProperty=fullName>   
 [MaskedTextBox コントロール](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)   
 [正規表現の例](../../../docs/standard/base-types/regular-expression-examples.md)