---
title: "ToolStrip コントロールのアーキテクチャ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ToolStrip コントロール [Windows フォーム], アーキテクチャ"
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
caps.latest.revision: 32
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 32
---
# ToolStrip コントロールのアーキテクチャ
<xref:System.Windows.Forms.ToolStrip> クラスと <xref:System.Windows.Forms.ToolStripItem> クラスには、ツール バー項目、ステータス項目、およびメニュー項目を表示するための柔軟で拡張性のあるシステムが実装されています。  これらのクラスはすべて <xref:System.Windows.Forms> 名前空間に格納されており、通常、名前にはすべて "ToolStrip" プリフィックス \(<xref:System.Windows.Forms.ToolStripOverflow> など\) または "Strip" サフィックス \(<xref:System.Windows.Forms.MenuStrip> など\) が付きます。  
  
## ToolStrip  
 このトピックでは、<xref:System.Windows.Forms.ToolStrip> およびこのクラスから派生するコントロールについて説明します。  
  
 <xref:System.Windows.Forms.ToolStrip> は、<xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.StatusStrip>、および <xref:System.Windows.Forms.ContextMenuStrip> の抽象基本クラスです。  次のオブジェクト モデルは、<xref:System.Windows.Forms.ToolStrip> 継承階層構造を示しています。  
  
 ![ToolStrip オブジェクト モデル](../../../../docs/framework/winforms/controls/media/toolstripobjectmodel.png "ToolStripObjectModel")  
ToolStrip オブジェクト モデル  
  
 <xref:System.Windows.Forms.ToolStrip> に含まれているすべての項目には、<xref:System.Windows.Forms.ToolStrip.Items%2A> コレクションを介してアクセスできます。  <xref:System.Windows.Forms.ToolStripDropDownItem> に含まれているすべての項目には、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> コレクションを介してアクセスできます。  <xref:System.Windows.Forms.ToolStrip> の派生クラスでは、<xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> プロパティを使用して、現在表示されている項目のみにアクセスすることもできます。  これらは、現在オーバーフロー メニューにない項目です。  
  
 次の項目は、すべての位置で <xref:System.Windows.Forms.ToolStripSystemRenderer> および <xref:System.Windows.Forms.ToolStripProfessionalRenderer> の両方とシームレスに連動するように特別にデザインされています。  これらは、<xref:System.Windows.Forms.ToolStrip> コントロールのデザイン時に既定で使用できます。  
  
-   <xref:System.Windows.Forms.ToolStripButton>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### MenuStrip  
 <xref:System.Windows.Forms.MenuStrip> は、<xref:System.Windows.Forms.MainMenu> に代わる最上位のコンテナーです。  これには、キー処理機能とマルチ ドキュメント インターフェイス \(MDI\) 機能も用意されています。  <xref:System.Windows.Forms.ToolStripDropDownItem> および <xref:System.Windows.Forms.ToolStripMenuItem> は <xref:System.Windows.Forms.ToolStripItem> から派生していますが、機能的には、<xref:System.Windows.Forms.MenuStrip> と連動します。  
  
 次の項目は、すべての位置で <xref:System.Windows.Forms.ToolStripSystemRenderer> および <xref:System.Windows.Forms.ToolStripProfessionalRenderer> の両方とシームレスに連動するように特別にデザインされています。  これらは、<xref:System.Windows.Forms.MenuStrip> コントロールのデザイン時に既定で使用できます。  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### StatusStrip  
 <xref:System.Windows.Forms.StatusStrip> は <xref:System.Windows.Forms.StatusBar> コントロールを置き換えます。  <xref:System.Windows.Forms.StatusStrip> の特別な機能には、カスタムのテーブル レイアウトや、フォームのサイズ変更グリップと移動グリップのサポートがあります。また、使用可能な領域を <xref:System.Windows.Forms.ToolStripStatusLabel> で自動的に設定できる `Spring` プロパティもあります。  
  
 次の項目は、すべての位置で <xref:System.Windows.Forms.ToolStripSystemRenderer> および <xref:System.Windows.Forms.ToolStripProfessionalRenderer> の両方とシームレスに連動するように特別にデザインされています。  これらは、<xref:System.Windows.Forms.StatusStrip> コントロールのデザイン時に既定で使用できます。  
  
-   <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip> は <xref:System.Windows.Forms.ContextMenu> に代わるものです。  <xref:System.Windows.Forms.ContextMenuStrip> は任意のコントロールに関連付けることができ、関連付けたコントロールでは、マウスの右クリックで自動的にコンテキスト メニュー \(ショートカット メニュー\) が表示されます。  <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> を使用して、<xref:System.Windows.Forms.ContextMenuStrip> をプログラムによって表示できます。  <xref:System.Windows.Forms.ContextMenuStrip> では、キャンセル可能な <xref:System.Windows.Forms.ToolStripDropDown.Opening> イベントと <xref:System.Windows.Forms.ToolStripDropDown.Closing> イベントがサポートされているため、動的な作成や複数クリックのシナリオを処理できます。  <xref:System.Windows.Forms.ContextMenuStrip> イメージ、メニュー項目のチェックの状態、テキスト、アクセス キー、ショートカット、およびカスケード メニューをサポートしています。  
  
 次の項目は、すべての位置で <xref:System.Windows.Forms.ToolStripSystemRenderer> および <xref:System.Windows.Forms.ToolStripProfessionalRenderer> の両方とシームレスに連動するように特別にデザインされています。  これらは、<xref:System.Windows.Forms.ContextMenuStrip> コントロールのデザイン時に既定で使用できます。  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### ToolStrip の汎用機能  
 このトピックでは、<xref:System.Windows.Forms.ToolStrip> と派生コントロールに共通の機能と動作について説明します。  
  
#### 描画  
 <xref:System.Windows.Forms.ToolStrip> コントロールには、カスタム描画を行う方法がいくつかあります。  他の Windows フォーム コントロールと同様に、<xref:System.Windows.Forms.ToolStrip> と <xref:System.Windows.Forms.ToolStripItem> のどちらにも、オーバーライド可能な `OnPaint` メソッドと `Paint` イベントがあります。  通常の描画と同様に、座標系はコントロールのクライアント領域を基準としています。つまり、コントロールの左上角が 0, 0 になります。  <xref:System.Windows.Forms.ToolStripItem> の `Paint` イベントと `OnPaint` メソッドは、他のコントロール描画イベントと同じように動作します。  
  
 <xref:System.Windows.Forms.ToolStrip> コントロールでは、<xref:System.Windows.Forms.ToolStripRenderer> クラスを使用することにより、項目やコンテナーの描画の細部にアクセスすることもできます。このクラスには、<xref:System.Windows.Forms.ToolStrip> の背景、項目の背景、項目のイメージ、項目の矢印、項目のテキスト、および境界を描画するためのオーバーライド可能なメソッドがあります。  これらのメソッドのイベント引数は、四角形、色、テキスト形式など、目的に応じて調整できるいくつかのプロパティを公開します。  
  
 項目が描画される方法についてのいくつかの側面を調整するには、通常、<xref:System.Windows.Forms.ToolStripRenderer> をオーバーライドします。  
  
 新しい項目を作成していて、描画に関するすべての側面を制御する場合には、`OnPaint` メソッドをオーバーライドします。  `OnPaint` 内から、<xref:System.Windows.Forms.ToolStripRenderer> のメソッドを使用できます。  
  
 既定では、<xref:System.Windows.Forms.ToolStrip> は <xref:System.Windows.Forms.ControlStyles> 設定を利用してダブル バッファリングを行います。  
  
#### ペアレンティング  
 コンテナーの所有権とペアレンティングの概念は、他の Windows フォーム コンテナー コントロールよりも <xref:System.Windows.Forms.ToolStrip> コントロールの方が複雑です。  これは、オーバーフローなどの動的なシナリオをサポートし、複数の <xref:System.Windows.Forms.ToolStrip> 項目でドロップダウン項目を共有する場合や、コントロールからの <xref:System.Windows.Forms.ContextMenuStrip> の生成をサポートする場合に必要です。  
  
 次の一覧は、ペアレンティングに関連するメンバーとその使用方法を示しています。  
  
-   <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A> は、ドロップダウン項目のソースの項目にアクセスします。  これは <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> に似ていますが、コントロールを返すのではなく、<xref:System.Windows.Forms.ToolStripItem> を返します。  
  
-   <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> は、複数のコントロールが同じ <xref:System.Windows.Forms.ContextMenuStrip> を共有している場合に、どのコントロールが <xref:System.Windows.Forms.ContextMenuStrip> のソースであるかを決定します。  
  
-   <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A> は、<xref:System.Windows.Forms.ToolStripItem.Parent%2A> プロパティの読み取り専用アクセサーです。  親は所有者とは異なり、項目が表示される現在の <xref:System.Windows.Forms.ToolStrip> を表します。これはオーバーフロー領域の場合もあります。  
  
-   <xref:System.Windows.Forms.ToolStripItem.Owner%2A> は、項目コレクションに現在の <xref:System.Windows.Forms.ToolStripItem> を含む <xref:System.Windows.Forms.ToolStrip> を返します。  この方法は、オーバーフローを処理する特別なコードを記述せずに、トップレベルの <xref:System.Windows.Forms.ToolStrip> で <xref:System.Windows.Forms.ToolStrip.ImageList%2A> や他のプロパティを参照するのに最適です。  
  
#### 継承したコントロールの動作  
 次のコントロールは、継承で使用されると常にロックされます。  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.ToolStripContainer> のパネルなどの <xref:System.Windows.Forms.ToolStripPanel> と個々の <xref:System.Windows.Forms.ToolStripPanel> コントロール  
  
 たとえば、前の一覧にあるコントロールの 1 つまたは複数を使用して、新しい Windows フォーム アプリケーションを作成します。  1 つ以上のコントロールのアクセス修飾子を `public` または `protected` に設定し、プロジェクトをビルドします。  最初のフォームから継承するフォームを追加し、継承したコントロールを選択します。  このコントロールはロックされた状態で表示され、アクセス修飾子が `private` であるかのように動作します。  
  
#### ToolStripContainer の継承のサポート  
 <xref:System.Windows.Forms.ToolStripContainer> コントロールは、次の例のような限定された継承のシナリオをサポートしています。  
  
1.  新しい Windows フォームアプリケーションを作成します。  
  
2.  フォームに <xref:System.Windows.Forms.ToolStripContainer> を追加します。  
  
3.  <xref:System.Windows.Forms.ToolStripContainer> のアクセス修飾子を `public` または `protected` に設定します。  
  
4.  <xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.ContextMenuStrip> の各コントロールを任意に組み合わせて、<xref:System.Windows.Forms.ToolStripContainer> の <xref:System.Windows.Forms.ToolStripPanel> 領域に追加します。  
  
5.  プロジェクトをビルドします。  
  
6.  最初のフォームから継承するフォームを追加します。  
  
7.  継承した <xref:System.Windows.Forms.ToolStripContainer> をフォーム上で選択します。  
  
#### 子コントロールの継承の動作  
 前の手順を完了すると、次のような継承の動作が発生します。  
  
-   デザイナーには、継承したアイコンと一緒にコントロールが表示されます。  
  
-   <xref:System.Windows.Forms.ToolStripPanel> コントロールはロックされます。コンテンツの選択や再配置を行うことはできません。  
  
-   コントロールは、<xref:System.Windows.Forms.ToolStripContentPanel> に追加したり移動したりできます。また、<xref:System.Windows.Forms.ToolStripContentPanel> の子コントロールすることもできます。  
  
-   変更内容はフォームのビルド後も保持されます。  
  
    > [!NOTE]
    >  削除する必要がある場合は、<xref:System.Windows.Forms.ToolStripContainer> に含まれているすべての <xref:System.Windows.Forms.ToolStripPanel> コントロールから、アクセス修飾子を削除してください。  この場合は、<xref:System.Windows.Forms.ToolStripContainer> のアクセス修飾子によってコントロール全体が制御されます。  
  
#### 部分信頼  
 部分的にしか信頼のない状況では、不用意に入力した個人情報が認証されていない個人やサービスから使われることのないように、`ToolStrip` に制限が適用されます。  次のような保護方法があります。  
  
-   `ToolStripDropDown` コントロールで <xref:System.Windows.Forms.ToolStripControlHost> の項目を表示するには、<xref:System.Security.Permissions.UIPermissionWindow> が必要です。  これは、<xref:System.Windows.Forms.ToolStripTextBox>、<xref:System.Windows.Forms.ToolStripComboBox>、<xref:System.Windows.Forms.ToolStripProgressBar> などの組み込みコントロールだけでなく、ユーザーが作成したコントロールにも適用されます。  この要件に適合しない場合、このような項目は表示されません。  例外をスローすることはありません。  
  
-   <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> プロパティを `false` に設定することはできません。また、キャンセル可能な <xref:System.Windows.Forms.ToolStripDropDown.Closing> イベント パラメーターは無視されます。  このため、ドロップダウン項目を表示したまま複数のキーストロークを入力することはできなくなります。  この要件に適合しない場合、このような項目は表示されません。  例外をスローすることはありません。  
  
-   <xref:System.Security.Permissions.UIPermissionWindow> 以外の部分信頼の状況でキーストロークが発生しても、多くのキーストローク処理イベントは生成されません。  
  
-   <xref:System.Security.Permissions.UIPermissionWindow> が付与されていない場合、アクセス キーは処理されません。  
  
#### 使用方法  
 次の使用パターンは、<xref:System.Windows.Forms.ToolStrip> のレイアウト、キーボードの対話的操作、およびエンド ユーザーの動作に影響します。  
  
-   <xref:System.Windows.Forms.ToolStripPanel> への追加  
  
     <xref:System.Windows.Forms.ToolStrip> は、<xref:System.Windows.Forms.ToolStripPanel> 内および <xref:System.Windows.Forms.ToolStripPanel> 間に移動できます。  `Dock` プロパティは無視されます。また、<xref:System.Windows.Forms.ToolStrip.Stretch%2A> プロパティが `false` の場合は、項目が <xref:System.Windows.Forms.ToolStripPanel> に追加されるたびに <xref:System.Windows.Forms.ToolStrip> のサイズが増加します。  通常、<xref:System.Windows.Forms.ToolStrip> はタブ オーダーに含められません。  
  
-   ドッキング  
  
     <xref:System.Windows.Forms.ToolStrip> はコンテナーの一辺の固定位置に配置され、サイズがドッキング対象の辺全体に拡張されます。  通常、<xref:System.Windows.Forms.ToolStrip> はタブ オーダーに含められません。  
  
-   絶対配置  
  
     他のコントロールと同様に、<xref:System.Windows.Forms.ToolStrip> は <xref:System.Windows.Forms.Control.Location%2A> プロパティによって配置され、サイズが固定され、通常はタブ オーダーに含められます。  
  
#### キーボードによる対話操作  
  
##### アクセス キー  
 Alt キーと同時または Alt キーに続けてアクセス キーを入力する操作は、キーボードを使用してコントロールをアクティブ化する 1 つの方法です。  <xref:System.Windows.Forms.ToolStrip> では、明示的および暗黙的なアクセス キーの両方がサポートされます。  明示的な定義では、文字の前にアンパサンド \(&\) 文字を付けます。  暗黙的な定義では、指定された `Text` プロパティの文字の順序に基づいて、一致する項目を検出するアルゴリズムが使用されます。  
  
##### ショートカット キー  
 <xref:System.Windows.Forms.MenuStrip> で使用するショートカット キーは、<xref:System.Windows.Forms.Keys> 列挙値 \(順序が特定されているわけではありません\) の組み合わせを使用して定義します。  また、<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> プロパティを使用すると、テキストのみを使用してショートカット キーを表示できます。たとえば、"Delete" の代わりに "Del" と表示できます。  
  
##### Navigation  
 Alt キーは、<xref:System.Windows.Forms.Form.MainMenuStrip%2A> で指定される <xref:System.Windows.Forms.MenuStrip> をアクティブ化します。  この状態で Ctrl \+ Tab キーを使用すると、`ToolStripPanel` 内の <xref:System.Windows.Forms.ToolStrip> コントロール間を移動できます。  Tab キーおよびテンキーの方向キーを使用すると、<xref:System.Windows.Forms.ToolStrip> の項目間を移動できます。  オーバーフロー領域の移動は、特別なアルゴリズムによって処理されます。  Space キーを押すと、<xref:System.Windows.Forms.ToolStripButton>、<xref:System.Windows.Forms.ToolStripDropDownButton>、または <xref:System.Windows.Forms.ToolStripSplitButton> が選択されます。  
  
##### フォーカスと検証  
 Alt キーで <xref:System.Windows.Forms.MenuStrip> または <xref:System.Windows.Forms.ToolStrip> をアクティブ化しても、通常、現在フォーカスがあるコントロールからフォーカスが移動したり削除されたりすることはありません。  <xref:System.Windows.Forms.MenuStrip> 内でホストされているコントロールまたは <xref:System.Windows.Forms.MenuStrip> のドロップダウンがある場合、ユーザーが Tab キーを押すとコントロールはフォーカスを取得します。  一般的に、<xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.Control.GotFocus>、<xref:System.Windows.Forms.Control.LostFocus>、<xref:System.Windows.Forms.Control.Enter>、<xref:System.Windows.Forms.Control.Leave> の各イベントは、キーボードでアクティブ化した場合は発生しません。  このような場合は、代わりに <xref:System.Windows.Forms.MenuStrip.MenuActivate> イベントと <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> イベントを使用します。  
  
 既定では、<xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> は `false` に設定されています。  検証を実行するには、フォームで明示的に <xref:System.Windows.Forms.ContainerControl.Validate%2A> を呼び出します。  
  
#### \[レイアウト\]  
 <xref:System.Windows.Forms.ToolStrip> のレイアウトを制御するには、<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> プロパティで <xref:System.Windows.Forms.ToolStripLayoutStyle> のメンバーの 1 つを選択します。  
  
##### スタック レイアウト  
 スタックとは、<xref:System.Windows.Forms.ToolStrip> の両端が互いに密着するように項目を配置することです。  次の一覧に、スタック レイアウトの説明を示します。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle> が既定値です。  この設定により、<xref:System.Windows.Forms.ToolStrip> は、<xref:System.Windows.Forms.ToolStrip.Orientation%2A> プロパティに従ってそのレイアウトを自動的に変更し、ドラッグおよびドッキングのシナリオに対応します。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle> は、<xref:System.Windows.Forms.ToolStrip> の項目を縦方向に並べて描画します。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle> は、<xref:System.Windows.Forms.ToolStrip> の項目を横方向に並べて描画します。  
  
##### スタック レイアウトのその他の機能  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> は、項目が配置される <xref:System.Windows.Forms.ToolStrip> の末尾を決定します。  
  
 項目が <xref:System.Windows.Forms.ToolStrip> 内に収まらない場合は、オーバーフロー ボタンが自動的に表示されます。  <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> プロパティの設定によって、項目を常にオーバーフロー領域に表示する、必要な場合のみ表示する、または表示しないのいずれかに決定します。  
  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> イベントでは、<xref:System.Windows.Forms.ToolStripItem.Placement%2A> プロパティを調べ、項目がメインの <xref:System.Windows.Forms.ToolStrip> とオーバーフロー状態の <xref:System.Windows.Forms.ToolStrip> のどちらに配置されているか、または現在はまったく表示されていないかを確認できます。  項目が表示されない典型的な理由は、項目がメインの <xref:System.Windows.Forms.ToolStrip> に収まらず、その <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> プロパティが <xref:System.Windows.Forms.ToolStripItemOverflow> に設定されていることです。  
  
 <xref:System.Windows.Forms.ToolStrip> を移動できるようにするには、これを <xref:System.Windows.Forms.ToolStripPanel> に配置し、その <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> を <xref:System.Windows.Forms.ToolStripGripStyle> に設定します。  
  
##### その他のレイアウト オプション  
 その他のレイアウト オプションとして、<xref:System.Windows.Forms.ToolStripLayoutStyle> および <xref:System.Windows.Forms.ToolStripLayoutStyle> があります。  
  
##### フロー レイアウト  
 <xref:System.Windows.Forms.ContextMenuStrip>、<xref:System.Windows.Forms.ToolStripDropDownMenu>、および <xref:System.Windows.Forms.ToolStripOverflow> の場合は、<xref:System.Windows.Forms.ToolStripLayoutStyle> が既定のレイアウトです。  このレイアウトは、<xref:System.Windows.Forms.FlowLayoutPanel> に似ています。  <xref:System.Windows.Forms.ToolStripLayoutStyle> レイアウトの機能は次のとおりです。  
  
-   <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> プロパティによって、<xref:System.Windows.Forms.FlowLayoutPanel> のすべての機能が公開されています。  <xref:System.Windows.Forms.LayoutSettings> クラスを <xref:System.Windows.Forms.FlowLayoutSettings> クラスにキャストする必要があります。  
  
-   コード内で <xref:System.Windows.Forms.ToolStripItem.Dock%2A> プロパティおよび <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> プロパティを使用して、項目を行内に配置できます。  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> プロパティは無視されます。  
  
-   <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> イベントでは、<xref:System.Windows.Forms.ToolStripItem.Placement%2A> プロパティを調べ、項目がメインの <xref:System.Windows.Forms.ToolStrip> に配置されたか、収まらなかったかを確認できます。  
  
-   グリップが描画されないため、<xref:System.Windows.Forms.ToolStripPanel> にある <xref:System.Windows.Forms.ToolStripLayoutStyle> レイアウト スタイルの <xref:System.Windows.Forms.ToolStrip> を移動できません。  
  
-   <xref:System.Windows.Forms.ToolStrip> オーバーフロー ボタンは描画されません。また、<xref:System.Windows.Forms.ToolStripItem.Overflow%2A> は無視されます。  
  
##### テーブル レイアウト  
 <xref:System.Windows.Forms.StatusStrip> の場合は、<xref:System.Windows.Forms.ToolStripLayoutStyle> が既定のレイアウトです。  このレイアウトは、<xref:System.Windows.Forms.TableLayoutPanel> に似ています。  <xref:System.Windows.Forms.ToolStripLayoutStyle> レイアウトの機能は次のとおりです。  
  
-   <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> プロパティによって、<xref:System.Windows.Forms.TableLayoutPanel> のすべての機能が公開されています。  <xref:System.Windows.Forms.LayoutSettings> クラスを <xref:System.Windows.Forms.TableLayoutSettings> クラスにキャストする必要があります。  
  
-   コード内で <xref:System.Windows.Forms.ToolStripItem.Dock%2A> プロパティおよび <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> プロパティを使用して、項目をテーブルのセル内に配置できます。  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> プロパティは無視されます。  
  
-   <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> イベントでは、<xref:System.Windows.Forms.ToolStripItem.Placement%2A> プロパティを調べ、項目がメインの <xref:System.Windows.Forms.ToolStrip> に配置されたか、収まらなかったかを確認できます。  
  
-   グリップが描画されないため、<xref:System.Windows.Forms.ToolStripPanel> の <xref:System.Windows.Forms.ToolStripLayoutStyle> レイアウト スタイルでは <xref:System.Windows.Forms.ToolStrip> を削除できません。  
  
-   <xref:System.Windows.Forms.ToolStrip> オーバーフロー ボタンは描画されません。また、<xref:System.Windows.Forms.ToolStripItem.Overflow%2A> は無視されます。  
  
## ToolStripItem  
 このトピックでは、<xref:System.Windows.Forms.ToolStripItem> およびこのクラスから派生するコントロールについて説明します。  
  
 <xref:System.Windows.Forms.ToolStripItem> は、<xref:System.Windows.Forms.ToolStrip> に追加されるすべての項目に対する抽象基本クラスです。  次のオブジェクト モデルは、<xref:System.Windows.Forms.ToolStripItem> 継承階層構造を示しています。  
  
 ![ToolStripItem オブジェクト モデル](../../../../docs/framework/winforms/controls/media/toolstripitemobjectmodel.png "ToolStripItemObjectModel")  
ToolStripItem オブジェクト モデル  
  
 <xref:System.Windows.Forms.ToolStripItem> クラスは、<xref:System.Windows.Forms.ToolStripItem> から直接継承するか、<xref:System.Windows.Forms.ToolStripControlHost> または <xref:System.Windows.Forms.ToolStripDropDownItem> を介して <xref:System.Windows.Forms.ToolStripItem> から間接的に継承します。  
  
 <xref:System.Windows.Forms.ToolStripItem> コントロールは、<xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.StatusStrip>、または <xref:System.Windows.Forms.ContextMenuStrip> に格納される必要があり、フォームに直接追加できません。  <xref:System.Windows.Forms.ToolStripItem> コントロールの適切なサブセットを含むさまざまなコンテナー クラスが設計されています。  
  
 <xref:System.Windows.Forms.ToolStripItem> ストック コントロールおよびこれらのコントロールが最適に表示されるコンテナーを次の表に示します。  <xref:System.Windows.Forms.ToolStrip> 項目は <xref:System.Windows.Forms.ToolStrip> の派生コンテナーであればどれでもホストできますが、以下に示すコンテナー内で最適に表示されるように設計されています。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown> は、デザイナー ツールボックスには表示されません。  
  
|含まれる項目|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|  
|------------|---------------|---------------|----------------------|-----------------|-----------------------|  
|<xref:System.Windows.Forms.ToolStripButton>|○|Ｘ|Ｘ|Ｘ|○|  
|<xref:System.Windows.Forms.ToolStripComboBox>|○|○|○|Ｘ|○|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|○|Ｘ|Ｘ|○|○|  
|<xref:System.Windows.Forms.ToolStripLabel>|○|Ｘ|Ｘ|○|○|  
|<xref:System.Windows.Forms.ToolStripSeparator>|○|○|○|Ｘ|○|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|○|Ｘ|Ｘ|○|○|  
|<xref:System.Windows.Forms.ToolStripTextBox>|○|○|○|Ｘ|○|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Ｘ|○|○|Ｘ|Ｘ|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Ｘ|Ｘ|Ｘ|○|Ｘ|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|○|Ｘ|Ｘ|○|Ｘ|  
|<xref:System.Windows.Forms.ToolStripControlHost>|○|○|Ｘ|○|○|  
  
### ToolStripButton  
 <xref:System.Windows.Forms.ToolStripButton> は <xref:System.Windows.Forms.ToolStrip> のボタン項目です。  さまざまな境界線スタイルで表示でき、操作状態を表したりアクティブ化したりするためにも使用できます。  既定でフォーカスが設定されるように定義することもできます。  
  
### ToolStripLabel  
 <xref:System.Windows.Forms.ToolStripLabel> は、<xref:System.Windows.Forms.ToolStrip> コントロールにラベル機能を提供します。  <xref:System.Windows.Forms.ToolStripLabel> は <xref:System.Windows.Forms.ToolStripButton> と似ており、既定ではフォーカスが設定されず、押下または強調表示された状態として描画されることもありません。  
  
 ホストされる項目としての <xref:System.Windows.Forms.ToolStripLabel> では、アクセス キーがサポートされます。  
  
 <xref:System.Windows.Forms.ToolStrip> でリンク コントロールをサポートするには、<xref:System.Windows.Forms.ToolStripLabel> の <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>、<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>、<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> の各プロパティを使用します。  
  
### ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel> は、<xref:System.Windows.Forms.StatusStrip> で使用するように特別に設計されたバージョンの <xref:System.Windows.Forms.ToolStripLabel> です。  固有の機能として、<xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>、<xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>、および <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> があります。  
  
### ToolStripSeparator  
 <xref:System.Windows.Forms.ToolStripSeparator> は、ツール バーまたはメニューの方向に応じて、縦線または横線を追加します。  メニュー項目など、項目間のグループ化や区切りに使用できます。  
  
 <xref:System.Windows.Forms.ToolStripSeparator> を追加するには、デザイン時にドロップダウン リストから選択します。  ただし、デザイナーのテンプレート ノードまたは <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> メソッドでハイフン \(\-\) を入力することで、自動的に <xref:System.Windows.Forms.ToolStripSeparator> を作成することもできます。  
  
### ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost> は、<xref:System.Windows.Forms.ToolStripComboBox>、<xref:System.Windows.Forms.ToolStripTextBox>、および <xref:System.Windows.Forms.ToolStripProgressBar> の抽象基本クラスです。  <xref:System.Windows.Forms.ToolStripControlHost> は、カスタム コントロールを含む他のコントロールを次の 2 つの方法でホストできます。  
  
-   <xref:System.Windows.Forms.Control> から派生するクラスを使用して <xref:System.Windows.Forms.ToolStripControlHost> を構築します。  ホストされるコントロールおよびプロパティに完全にアクセスするには、<xref:System.Windows.Forms.ToolStripControlHost.Control%2A> プロパティをキャストして、このプロパティが表す実際のクラスに戻す必要があります。  
  
-   <xref:System.Windows.Forms.ToolStripControlHost> を拡張し、継承クラスの既定のコンストラクター内で、<xref:System.Windows.Forms.Control> から派生したクラスを渡す基本クラス コンストラクターを呼び出します。  このオプションを使用して一般的なコントロール メソッドとプロパティをラップすると、<xref:System.Windows.Forms.ToolStrip> 内でのアクセスが簡単になります。  
  
### ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox> は、<xref:System.Windows.Forms.ToolStrip> でホストするために最適化された <xref:System.Windows.Forms.ComboBox> です。  ホストされるコントロールのプロパティとイベントのサブセットは <xref:System.Windows.Forms.ToolStripComboBox> レベルで公開されますが、基になる <xref:System.Windows.Forms.ComboBox> コントロールは <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> プロパティを使用して完全にアクセスできます。  
  
### ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox> は、<xref:System.Windows.Forms.ToolStrip> でホストするために最適化された <xref:System.Windows.Forms.TextBox> です。  ホストされるコントロールのプロパティとイベントのサブセットは <xref:System.Windows.Forms.ToolStripTextBox> レベルで公開されますが、基になる <xref:System.Windows.Forms.TextBox> コントロールは <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> プロパティを使用して完全にアクセスできます。  
  
### ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar> は、<xref:System.Windows.Forms.ToolStrip> でホストするために最適化された <xref:System.Windows.Forms.ProgressBar> です。  ホストされるコントロールのプロパティとイベントのサブセットは <xref:System.Windows.Forms.ToolStripProgressBar> レベルで公開されますが、基になる <xref:System.Windows.Forms.ProgressBar> コントロールは <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> プロパティを使用して完全にアクセスできます。  
  
### ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem> は、<xref:System.Windows.Forms.ToolStripMenuItem>、<xref:System.Windows.Forms.ToolStripDropDownButton>、および <xref:System.Windows.Forms.ToolStripSplitButton> の抽象基本クラスです。項目を直接ホストしたり、ドロップダウン コンテナーで追加項目をホストしたりできます。  これを実行するには、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> プロパティを <xref:System.Windows.Forms.ToolStripDropDown> に設定して、<xref:System.Windows.Forms.ToolStripDropDown> の <xref:System.Windows.Forms.ToolStrip.Items%2A> プロパティを設定します。  これらのドロップダウン項目には、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> プロパティを使用して直接アクセスできます。  
  
### ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem> は、<xref:System.Windows.Forms.ToolStripDropDownMenu> や <xref:System.Windows.Forms.ContextMenuStrip> と連携して、メニューの特殊な強調表示、レイアウト、および列の配置を処理する <xref:System.Windows.Forms.ToolStripDropDownItem> です。  
  
### ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton> は <xref:System.Windows.Forms.ToolStripButton> に似ていますが、ユーザーがクリックするとドロップダウン領域が表示される点が異なります。  <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> プロパティを設定することで、ドロップダウン矢印を表示または非表示にできます。  <xref:System.Windows.Forms.ToolStripDropDownButton> は、<xref:System.Windows.Forms.ToolStrip> をオーバーフローする項目を表示する <xref:System.Windows.Forms.ToolStripOverflowButton> をホストします。  
  
### ToolStripSplitButton  
 <xref:System.Windows.Forms.ToolStripSplitButton> は、ボタンとドロップダウン ボタンの機能を組み合わせます。  
  
 <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> プロパティを使用して、選択されたドロップダウン項目に対応する <xref:System.Windows.Forms.Control.Click> イベントと、ボタンに表示される項目とを同期します。  
  
### ToolStripItem の汎用機能  
 <xref:System.Windows.Forms.ToolStripItem> には、次のように、継承するコントロールに共通の機能とオプションがあります。  
  
-   コア イベント  
  
-   イメージ処理  
  
-   \[配置\]  
  
-   テキストとイメージの関係  
  
-   表示スタイル  
  
#### コア イベント  
 <xref:System.Windows.Forms.ToolStripItem> では、自身に対するクリック イベント、マウス イベント、および描画イベントを受け取り、なんらかのキーボードの前処理を実行することもできます。  
  
#### イメージ処理  
 <xref:System.Windows.Forms.ToolStripItem.Image%2A>、<xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>、<xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>、<xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>、<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> の各プロパティは、イメージ処理のさまざまな要素に関連しています。  <xref:System.Windows.Forms.ToolStrip> コントロールでイメージを使用するには、これらのプロパティを手動で設定するか、実行時のみに有効な <xref:System.Windows.Forms.ToolStrip.ImageList%2A> プロパティを設定します。  
  
 イメージのスケーリングは、次のように、<xref:System.Windows.Forms.ToolStrip> および <xref:System.Windows.Forms.ToolStripItem> の両方のプロパティの相互作用によって決まります。  
  
-   <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A> は、イメージの <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> の設定とコンテナーの <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> の設定の組み合わせによって決まる、最終的なイメージのスケールです。  
  
    -   <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> が `true` \(既定\) で <xref:System.Windows.Forms.ToolStripItemImageScaling> が <xref:System.Windows.Forms.ToolStripItemImageScaling> の場合、イメージの拡大と縮小は行われず、<xref:System.Windows.Forms.ToolStrip> のサイズは最大の項目と同じサイズまたは定義済みの最小サイズになります。  
  
    -   <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> が `false` で <xref:System.Windows.Forms.ToolStripItemImageScaling> が <xref:System.Windows.Forms.ToolStripItemImageScaling> の場合、イメージや <xref:System.Windows.Forms.ToolStrip> の拡大と縮小は行われません。  
  
#### \[配置\]  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> プロパティの値は、項目を表示する <xref:System.Windows.Forms.ToolStrip> の辺を決定します。  <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> プロパティが機能するのは、<xref:System.Windows.Forms.ToolStrip> のレイアウト スタイルがスタック オーバーフロー値のいずれかに設定されている場合のみです。  
  
 項目は、項目コレクションに表示される順序で <xref:System.Windows.Forms.ToolStrip> に配置されます。  項目を配置する場所をプログラムで変更するには、<xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> メソッドを使用してコレクションの項目を移動します。  このメソッドは項目を移動しますが、複製はしません。  
  
#### テキストとイメージの関係  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> プロパティは、<xref:System.Windows.Forms.ToolStripItem> 上のテキストに対するイメージの相対的位置を定義します。  イメージ、テキスト、またはその両方がない項目は、<xref:System.Windows.Forms.ToolStripItem> で存在しない要素の代わりに空白が表示されないように、特別なケースとして扱われます。  
  
#### 表示スタイル  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> を使用すると、項目の Text プロパティと Image プロパティの値を設定して必要なものだけを表示できます。  これは通常、同じ項目を異なるコンテキストで表示するとき、表示スタイルだけを変更するために使用されます。  
  
## アクセサリ クラス  
 次のように、他にもさまざまな機能を実現するクラスがあります。  
  
-   <xref:System.Windows.Forms.ToolStripManager> は、アプリケーション全体について <xref:System.Windows.Forms.ToolStrip> 関連のタスクをサポートします。たとえば、マージ、設定、レンダラーのオプションなどがあります。  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> を使用すると、特定のスタイルやテーマを簡単に <xref:System.Windows.Forms.ToolStrip> に適用できます。  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> は、置き換えることのできるカラー テーブル \(<xref:System.Windows.Forms.ProfessionalColorTable>\) に基づいてペンとブラシを作成します。  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> は、システム カラーとフラットな visual スタイルを <xref:System.Windows.Forms.ToolStrip> アプリケーションに適用します。  
  
-   <xref:System.Windows.Forms.ToolStripContainer> は <xref:System.Windows.Forms.SplitContainer> と似ています。  ドッキング対象の 4 つのサイド パネル \(<xref:System.Windows.Forms.ToolStripPanel> のインスタンス\) と、1 つのセントラル パネル \(<xref:System.Windows.Forms.ToolStripContentPanel> のインスタンス\) を使用して、一般的な配置が作成されます。  サイド パネルは削除できませんが、非表示にすることはできます。  セントラル パネルを削除または非表示にすることはできません。  1 つ以上の <xref:System.Windows.Forms.ToolStrip> コントロール、<xref:System.Windows.Forms.MenuStrip> コントロール、または <xref:System.Windows.Forms.StatusStrip> コントロールをサイド パネルに配置でき、他のコントロールにはセントラル パネルを使用できます。  <xref:System.Windows.Forms.ToolStripContentPanel> には、フォーム本体にレンダラーのサポートを取り入れ、一貫した状態で表示する方法も用意されています。  <xref:System.Windows.Forms.ToolStripContainer> はマルチ ドキュメント インターフェイス \(MDI\) をサポートしていません。  
  
-   <xref:System.Windows.Forms.ToolStripPanel> は、<xref:System.Windows.Forms.ToolStrip> コントロールを移動および配置する領域を作成します。  1 つのパネルだけを使用することもできますが、<xref:System.Windows.Forms.ToolStripPanel> は MDI のシナリオにも適しています。  
  
## 参照  
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)   
 [ToolStrip コントロール](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)   
 [MenuStrip コントロール](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)   
 [StatusStrip コントロール](../../../../docs/framework/winforms/controls/statusstrip-control.md)   
 [ContextMenuStrip コントロール](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)   
 [BindingNavigator コントロール](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)