---
title: "コントロールのフォーカスのスタイルと FocusVisualStyle | Microsoft Docs"
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
  - "キーボード フォーカス"
  - "フォーカスの外観のスタイル設定"
  - "フォーカス表示スタイルのスタイル"
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# コントロールのフォーカスのスタイルと FocusVisualStyle
\<?xml version="1.0" encoding="utf-8"?>
\<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <token>相互</token>がキーボード フォーカスを受け取ったときに、コントロールの外観を変更するための&2; つの並列メカニズムを提供します。最初のメカニズムはなどのプロパティをプロパティ set アクセス操作子を使用して、 <codeEntityReference autoUpgrade="true">P:System.Windows.UIElement.IsKeyboardFocused</codeEntityReference>スタイルまたはコントロールに適用されているテンプレート内で。2 番目の機構の値として個別のスタイルを提供する、 <codeEntityReference autoUpgrade="true">P:System.Windows.FrameworkElement.FocusVisualStyle</codeEntityReference>プロパティ「フォーカス表示スタイル」、置換することで、コントロールまたはその他の UI 要素のビジュアル ツリーを変更するのではなく、コントロールの上に描画される装飾には別個のビジュアル ツリーを作成します。このトピックでは、これらのメカニズムが適切なシナリオについて説明します。</para> 
    <para>
      <token>アウトラインの自動作成</token>
    </para>
  </introduction>
  <section address="Purpose">
    <title>目的のフォーカス表示スタイル</title>
    <content>
      <para>フォーカス表示スタイル機能は、UI 要素にキーボード ナビゲーションに基づいてビジュアルのユーザーからのフィードバックを導入するため共通「オブジェクト モデル」を提供します。新しいテンプレートをコントロールに適用するか、特定のテンプレート構成を知ることがなく可能です。</para>
      <para>フォーカス表示スタイル機能は、コントロール テンプレートを知らなくても機能するために正確にフォーカス表示スタイルを使用してコントロールの表示可能な視覚的なフィードバックが制限とは限りません。コントロールの描画、テンプレートを通じてによって作成されたビジュアル ツリーの上に別のビジュアル ツリー (装飾) をオーバーレイには、機能が実際にです。この次の値を格納するスタイルを使用して別個のビジュアル ツリーを定義する、 <codeEntityReference autoUpgrade="true">P:System.Windows.FrameworkElement.FocusVisualStyle</codeEntityReference>プロパティです。</para>
    </content>
  </section>
  <section address="Default">
    <title>既定のフォーカス ビジュアル スタイル動作</title>
    <content>
      <para>のみフォーカス操作が開始されたとき、キーボードでフォーカス表示スタイルの機能です。マウス操作やプログラムでのフォーカスが変更には、フォーカス表示スタイルのモードが無効にします。フォーカスのモードの違いの詳細については、次を参照してください\<link xlink:href="0230c4eb-0c8a-462b-ac4b-ae3e511659f4">フォーカス概要</link>。</para> 。
      <para>コントロールのテーマには、テーマでのすべてのコントロールのフォーカス表示スタイルになる既定フォーカス表示スタイルの動作が含まれます。このテーマ スタイルは、静的なキーの値によって識別される<codeEntityReference autoUpgrade="true">P:System.Windows.SystemParameters.FocusVisualStyleKey</codeEntityReference>します。アプリケーション レベルで、独自のフォーカス表示スタイルを宣言するときに、この既定のスタイルの動作のテーマからを置き換えます。または、全体のテーマを定義する場合は、テーマ全体の既定の動作の線のスタイルを定義するこれと同じキーを使用する必要があります。</para>
      <para>テーマ、既定のフォーカス表示スタイルが一般に非常にシンプルです。おおよその近似値を次に示します。</para>
      <code>&lt;Style x:Key="{x:Static SystemParameters.FocusVisualStyleKey}"&gt;
  &lt;Setter Property="Control.Template"&gt;
    &lt;Setter.Value&gt;
      &lt;ControlTemplate&gt;
        &lt;Rectangle StrokeThickness="1"
          Stroke="Black"
          StrokeDashArray="1 2"
          SnapsToDevicePixels="true"/&gt;
      &lt;/ControlTemplate&gt;
    &lt;/Setter.Value&gt;
  &lt;/Setter&gt;
&lt;/Style&gt;</code>
    </content>
  </section>
  <section address="When">
    <title>フォーカスの Visual スタイルを使用するタイミング</title>
    <content>
      <para>概念的には、コントロールに適用されるフォーカス表示スタイルの外観はで一貫しているコントロールをします。一貫性を実現する&1; つの方法では、コントロールから、テーマで定義されている各コントロールを取得、まったく同じフォーカス表示スタイル、またはスタイルのいくつかのバリエーションのいずれかを全体のテーマを作成する場合にのみ、visual スタイルが関連する視覚的にフォーカスをコントロールに変更します。ページや UI にキーボード フォーカスのすべての要素のスタイルを設定する同じスタイル (または同様のスタイル) を使用する場合があります。</para>
      <para>設定<codeEntityReference autoUpgrade="true">P:System.Windows.FrameworkElement.FocusVisualStyle</codeEntityReference>テーマの一部ではない個別のコントロールのスタイルでは、フォーカスの使用目的ではない視覚スタイル。これは、コントロール間の一貫性のない visual 動作は、キーボード フォーカスに関してユーザー エクスペリエンスに混乱する可能性があるためです。トリガー (スタイルの) などを使用して入力の状態をそれぞれのプロパティをはるかに優れた方法は、意図的に不整合があるテーマにわたって、キーボード フォーカス コントロール固有の動作をコントロールする場合<codeEntityReference autoUpgrade="true">において</codeEntityReference>または<codeEntityReference autoUpgrade="true">P:System.Windows.UIElement.IsKeyboardFocused</codeEntityReference>.</para>
      <para>フォーカス表示スタイルがキーボード フォーカス専用の機能です。そのため、フォーカス表示スタイルは、ユーザー補助機能の種類です。マウスを使用しているかどうか、フォーカスの任意の型の UI の変更をする場合はフォーカス表示スタイルを使用しないでくださいし、set アクセス操作子とスタイルやなどの全般的な焦点プロパティの値から作業するテンプレート内のトリガーを使用する必要がありますキーボード、またはプログラムを使用して、次を<languageKeyword>IsFocused</languageKeyword>または<languageKeyword>IsFocusWithin</languageKeyword>します。</para>
    </content>
  </section>
  <section address="How">
    <title>フォーカス表示スタイルを作成する方法</title>
    <content>
      <para>フォーカス表示スタイルがある用に作成する、スタイル、<codeEntityReference autoUpgrade="true">見ると</codeEntityReference>の<codeEntityReference autoUpgrade="true">動作</codeEntityReference>します。スタイルがの主要な要素で構成する必要があります、<codeEntityReference autoUpgrade="true">由来</codeEntityReference>します。フォーカス表示スタイルが割り当てられている型となる対象の型を指定しない、 <codeEntityReference autoUpgrade="true">P:System.Windows.FrameworkElement.FocusVisualStyle</codeEntityReference>.</para>
      <para>対象の型は常にため<codeEntityReference autoUpgrade="true">動作</codeEntityReference>、すべてのコントロールに共通するプロパティを使用してスタイルを設定する必要があります (のプロパティを使用して、<codeEntityReference autoUpgrade="true">動作</codeEntityReference>クラスとその基本クラス)。UI 要素にオーバーレイとして正しく機能して、コントロールの機能領域を隠さないテンプレートを作成する必要があります。一般に、この表示を意味する、視覚的なフィードバック必要がありますコントロールのマージンの外部またはコントロールのヒット テストがブロックされていない一時的または控え目な効果としてフォーカス表示スタイルが適用されます。テンプレート バインディングで使用できるサイズ変更とオーバーレイ テンプレートの配置を決定するのに便利なプロパティには、 <codeEntityReference autoUpgrade="true">P:System.Windows.FrameworkElement.ActualHeight</codeEntityReference>、 <codeEntityReference autoUpgrade="true">P:System.Windows.FrameworkElement.ActualWidth</codeEntityReference>、<codeEntityReference autoUpgrade="true">子</codeEntityReference>、および<codeEntityReference autoUpgrade="true">もう&1; つ</codeEntityReference>します。</para>
    </content>
  </section>
  <section address="Alternatives">
    <title>フォーカス表示スタイルを使用に代わる方法</title>
    <content>
      <para>フォーカス表示スタイルを使用してがない場合、適切ないずれかをスタイルを設定するための単一のコントロールまたはコントロール テンプレートをより細かく制御する必要があるためにがあるその他の多くのアクセス可能なプロパティやフォーカスのある変更に応じて、視覚的な動作を作成できる手法</para>。
      <para>トリガー、set アクセス操作子、およびイベントの set アクセス操作子がすべてで詳しく説明されている\<link xlink:href="481765e5-5467-4a75-9f7b-e10e2ac410d9">スタイルとテンプレート</link>します。ルーティング イベントの処理は、後ほど\<link xlink:href="1a2189ae-13b4-45b0-b12c-8de2e49c29d2">ルーティング イベントの概要</link>します。</para>
    </content>
    <sections>
      <section>
        <title>IsKeyboardFocused</title>
        <content>
          <para>にキーボード フォーカスを具体的には興味がある場合、 <codeEntityReference autoUpgrade="true">P:System.Windows.UIElement.IsKeyboardFocused</codeEntityReference>プロパティに対して依存関係プロパティを使用できる<codeEntityReference autoUpgrade="true">T:System.Windows.Trigger</codeEntityReference>します。スタイルまたはテンプレートのプロパティ トリガーは、1 つのコントロールについて非常に具体的には、必ずしも視覚的に一致しない他のコントロールのキーボード フォーカスの動作は、キーボード フォーカスの動作を定義するための適切な手法です。</para>
          <para>別のような依存関係プロパティが<codeEntityReference autoUpgrade="true">P:System.Windows.UIElement.IsKeyboardFocusWithin</codeEntityReference>、どこかに合成内またはコントロールの機能領域内では、視覚的に、そのキーボード フォーカスを呼び出そうとする場合に使用する適切なする必要があります。たとえば、配置することがあります、 <codeEntityReference autoUpgrade="true">P:System.Windows.UIElement.IsKeyboardFocusWithin</codeEntityReference>そのパネル内の個々 の要素上にあることなど、いくつかのコントロールをグループ化するパネルれる場合でも、キーボード フォーカスがより正確に可能性がありますが、異なるトリガー</para> 。
          <para>イベントを使用することもできます。 <codeEntityReference autoUpgrade="true">E:System.Windows.UIElement.GotKeyboardFocus</codeEntityReference>と<codeEntityReference autoUpgrade="true">E:System.Windows.UIElement.LostKeyboardFocus</codeEntityReference> (と同様に、プレビューの同等)。基準として、これらのイベントを使用することができます、<codeEntityReference autoUpgrade="true">可能な</codeEntityReference>、分離コードで、イベントのハンドラーを記述することもできます。</para>
        </content>
      </section>
      <section>
        <title>その他のフォーカス プロパティ</title>
        <content>
          <para>は setter を基本やをトリガーする必要がありますフォーカスを変更するすべての考えられる原因、視覚的な動作を作成する場合は、<codeEntityReference autoUpgrade="true">において</codeEntityReference>依存関係プロパティまたは上、<codeEntityReference autoUpgrade="true">また</codeEntityReference>または<codeEntityReference autoUpgrade="true">E:System.Windows.UIElement.LostFocus</codeEntityReference>に使用されるイベント、<codeEntityReference autoUpgrade="true">可能な</codeEntityReference>です。</para>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
\<link xlink:href="481765e5-5467-4a75-9f7b-e10e2ac410d9">スタイルとテンプレート</link>
\<link xlink:href="0230c4eb-0c8a-462b-ac4b-ae3e511659f4">フォーカスの概要</link>
\<link xlink:href="ee5258b7-6567-415a-9b1c-c0cbe46e79ef">入力の概要</link>
<codeEntityReference autoUpgrade="true">P:System.Windows.FrameworkElement.FocusVisualStyle</codeEntityReference>
\<legacyLink xlink:href="e7ec856e-41ee-47b1-9d57-b75a3dad088c">ユーザー補助機能</legacyLink>
</relatedTopics>
</developerConceptualDocument>