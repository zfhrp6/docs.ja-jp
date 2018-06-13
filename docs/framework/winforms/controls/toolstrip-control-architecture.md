---
title: ToolStrip コントロールのアーキテクチャ
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: fd00fff6c745f5f7991c038dec305b5d45761656
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542159"
---
# <a name="toolstrip-control-architecture"></a>ToolStrip コントロールのアーキテクチャ
<xref:System.Windows.Forms.ToolStrip>と<xref:System.Windows.Forms.ToolStripItem>クラスは、ツールバー、ステータス、およびメニュー項目を表示するため、柔軟な拡張可能なシステムを提供します。 これらのクラスはすべて、<xref:System.Windows.Forms>名前空間と、通常すべて"ToolStrip"プレフィックスを持つという名前 (など<xref:System.Windows.Forms.ToolStripOverflow>) または「ストリップ」サフィックスを持つ (など<xref:System.Windows.Forms.MenuStrip>)。  
  
## <a name="toolstrip"></a>ToolStrip  
 次のトピックについて説明<xref:System.Windows.Forms.ToolStrip>とそれから派生するコントロール。  
  
 <xref:System.Windows.Forms.ToolStrip> 抽象基本クラスは、 <xref:System.Windows.Forms.MenuStrip>、 <xref:System.Windows.Forms.StatusStrip>、および<xref:System.Windows.Forms.ContextMenuStrip>です。 次のオブジェクト モデルの表示、<xref:System.Windows.Forms.ToolStrip>継承階層です。  
  
 ![ToolStrip オブジェクト モデル](../../../../docs/framework/winforms/controls/media/toolstripobjectmodel.gif "ToolStripObjectModel")  
ToolStrip オブジェクト モデル  
  
 すべての項目にアクセスすることができます、<xref:System.Windows.Forms.ToolStrip>を通じて、<xref:System.Windows.Forms.ToolStrip.Items%2A>コレクション。 すべての項目にアクセスすることができます、<xref:System.Windows.Forms.ToolStripDropDownItem>を通じて、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A>コレクション。 派生したクラスで<xref:System.Windows.Forms.ToolStrip>、使用することも、<xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A>現在表示されている項目のみにアクセスするプロパティです。 これらは、オーバーフロー メニューに現在含まれていない項目です。  
  
 次の項目を両方とシームレスに動作する目的<xref:System.Windows.Forms.ToolStripSystemRenderer>と<xref:System.Windows.Forms.ToolStripProfessionalRenderer>すべての向きにします。 デザイン時に、既定では、<xref:System.Windows.Forms.ToolStrip>コントロール。  
  
-   <xref:System.Windows.Forms.ToolStripButton>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="menustrip"></a>MenuStrip  
 <xref:System.Windows.Forms.MenuStrip> 最上位のコンテナーを置き換える<xref:System.Windows.Forms.MainMenu>です。 これは、キーを処理し、複数のドキュメント インターフェイス (MDI) の機能も提供します。 機能的には、<xref:System.Windows.Forms.ToolStripDropDownItem>と<xref:System.Windows.Forms.ToolStripMenuItem>と共に職場<xref:System.Windows.Forms.MenuStrip>から派生しているが、<xref:System.Windows.Forms.ToolStripItem>です。  
  
 次の項目を両方とシームレスに動作する目的<xref:System.Windows.Forms.ToolStripSystemRenderer>と<xref:System.Windows.Forms.ToolStripProfessionalRenderer>すべての向きにします。 デザイン時に、既定では、<xref:System.Windows.Forms.MenuStrip>コントロール。  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="statusstrip"></a>StatusStrip  
 <xref:System.Windows.Forms.StatusStrip> 置換、<xref:System.Windows.Forms.StatusBar>コントロール。 特殊な機能<xref:System.Windows.Forms.StatusStrip>含めるカスタム テーブルのレイアウトは、フォームのサイズ変更や、グリップを移動のサポート、および`Spring`プロパティを<xref:System.Windows.Forms.ToolStripStatusLabel>使用可能な領域を自動的に入力します。  
  
 次の項目を両方とシームレスに動作する目的<xref:System.Windows.Forms.ToolStripSystemRenderer>と<xref:System.Windows.Forms.ToolStripProfessionalRenderer>すべての向きにします。 デザイン時に、既定では、<xref:System.Windows.Forms.StatusStrip>コントロール。  
  
-   <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### <a name="contextmenustrip"></a>ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip> 置換<xref:System.Windows.Forms.ContextMenu>です。 関連付けることができます、<xref:System.Windows.Forms.ContextMenuStrip>任意のコントロールとマウスの右クリック自動的に表示されます、コンテキスト メニュー (またはショートカット メニュー)。 表示することができます、<xref:System.Windows.Forms.ContextMenuStrip>を使用してプログラムで、<xref:System.Windows.Forms.ToolStripDropDown.Show%2A>メソッドです。 <xref:System.Windows.Forms.ContextMenuStrip> キャンセル可能なサポート<xref:System.Windows.Forms.ToolStripDropDown.Opening>と<xref:System.Windows.Forms.ToolStripDropDown.Closing>動的母集団と複数クリック シナリオを処理するイベントです。 <xref:System.Windows.Forms.ContextMenuStrip> イメージ、メニュー項目の状態の確認、テキスト、アクセス キー、ショートカット、およびカスケード メニューをサポートしています。  
  
 次の項目を両方とシームレスに動作する目的<xref:System.Windows.Forms.ToolStripSystemRenderer>と<xref:System.Windows.Forms.ToolStripProfessionalRenderer>すべての向きにします。 デザイン時に、既定では、<xref:System.Windows.Forms.ContextMenuStrip>コントロール。  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="toolstrip-generic-features"></a>ToolStrip の汎用機能  
 次のトピックは、機能とする一般的な動作について説明、<xref:System.Windows.Forms.ToolStrip>およびコントロールを派生します。  
  
#### <a name="painting"></a>描画  
 カスタム描画を行うことができます<xref:System.Windows.Forms.ToolStrip>いくつかの方法で制御します。 その他の Windows フォーム コントロールと同様、<xref:System.Windows.Forms.ToolStrip>と<xref:System.Windows.Forms.ToolStripItem>両方がオーバーライドできる`OnPaint`メソッドおよび`Paint`イベント。 コントロールのクライアント領域と相対的座標系は、通常の描画としてつまり、コントロールの左上隅には 0、0 です。 `Paint`イベントと`OnPaint`のメソッド、<xref:System.Windows.Forms.ToolStripItem>他のコントロールの描画イベントと同様に動作します。  
  
 <xref:System.Windows.Forms.ToolStrip>コントロールもアイテムおよびにより、そのコンテナーのレンダリングに細かいアクセスを提供、<xref:System.Windows.Forms.ToolStripRenderer>をバック グラウンド、項目の背景、項目のイメージ、項目 の矢印、項目のテキストの描画のオーバーライド可能なメソッドを持つ、クラスとの枠線と、<xref:System.Windows.Forms.ToolStrip>. これらのメソッドのイベント引数は、四角形、色、および必要に応じて調整できるテキスト形式などのいくつかのプロパティを公開します。  
  
 オーバーライドする通常の項目を描画する方法のいくつかの側面を調整する、<xref:System.Windows.Forms.ToolStripRenderer>です。  
  
 新しい項目を作成して、描画のすべての側面を制御する場合は、上書き、`OnPaint`メソッドです。 内から`OnPaint`からメソッドを使用することができます、<xref:System.Windows.Forms.ToolStripRenderer>です。  
  
 既定では、<xref:System.Windows.Forms.ToolStrip>はダブル バッファー内の活用、<xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>設定します。  
  
#### <a name="parenting"></a>親子関係  
 コンテナーの所有権およびペアレンティングの概念はでより複雑な<xref:System.Windows.Forms.ToolStrip>の他の Windows フォームのコンテナー コントロールよりも制御します。 オーバーフロー、複数のドロップダウン項目の共有などの動的なシナリオをサポートする必要がある<xref:System.Windows.Forms.ToolStrip>、項目の生成をサポートするために、<xref:System.Windows.Forms.ContextMenuStrip>コントロールからです。  
  
 次の一覧は、親子関係に関連するメンバーをについて説明し、それらの使用について説明します。  
  
-   <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A> ドロップダウンの項目のソースである項目にアクセスします。 これに似ています<xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>が返されたコントロールを返す代わりに、<xref:System.Windows.Forms.ToolStripItem>です。  
  
-   <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> どのコントロールが、ソースであることを決定の<xref:System.Windows.Forms.ContextMenuStrip>とき複数のコントロールが同じ<xref:System.Windows.Forms.ContextMenuStrip>です。  
  
-   <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A> 読み取り専用のアクセサーには、<xref:System.Windows.Forms.ToolStripItem.Parent%2A>プロパティです。 親は、親を表します返される現在の点で、所有者とは異なります。<xref:System.Windows.Forms.ToolStrip>アイテムが表示される、オーバーフロー領域になる場合があります。  
  
-   <xref:System.Windows.Forms.ToolStripItem.Owner%2A> 返します、<xref:System.Windows.Forms.ToolStrip>された項目コレクションには、現在が含まれています。<xref:System.Windows.Forms.ToolStripItem>です。 これを参照する最適な方法<xref:System.Windows.Forms.ToolStrip.ImageList%2A>または他のプロパティで、最上位<xref:System.Windows.Forms.ToolStrip>オーバーフローを処理する特別なコードを記述することがなくです。  
  
#### <a name="behavior-of-inherited-controls"></a>継承されたコントロールの動作  
 継承を使用するたびに、次のコントロールがロックされています。  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.ToolStripPanel> 内のパネルが含まれている、<xref:System.Windows.Forms.ToolStripContainer>とも個々<xref:System.Windows.Forms.ToolStripPanel>コントロール。  
  
 たとえば、前の一覧に 1 つ以上のコントロールを使用して、新しい Windows フォーム アプリケーションを作成します。 1 つまたは複数のコントロールのアクセス修飾子を設定`public`または`protected`、し、プロジェクトを作成します。 最初のフォームから継承したフォームを追加し、継承されたコントロールを選択します。 コントロールが表示され、アクセス修飾子が場合と同様の動作にロックされた`private`です。  
  
#### <a name="toolstripcontainer-support-of-inheritance"></a>ToolStripContainer の継承のサポート  
 <xref:System.Windows.Forms.ToolStripContainer>コントロールは次の例のように、制限付きの継承されたシナリオをサポートします。  
  
1.  新しい Windows フォーム アプリケーションを作成します。  
  
2.  フォームに <xref:System.Windows.Forms.ToolStripContainer> を追加します。  
  
3.  アクセス修飾子を設定、<xref:System.Windows.Forms.ToolStripContainer>に`public`または`protected`です。  
  
4.  任意の組み合わせを追加<xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.MenuStrip>、および<xref:System.Windows.Forms.ContextMenuStrip>コントロールを<xref:System.Windows.Forms.ToolStripPanel>の領域、<xref:System.Windows.Forms.ToolStripContainer>です。  
  
5.  プロジェクトをビルドします。  
  
6.  最初のフォームから継承したフォームを追加します。  
  
7.  継承された選択<xref:System.Windows.Forms.ToolStripContainer>フォームにします。  
  
#### <a name="inherited-behavior-of-child-controls"></a>子コントロールの継承の動作  
 前の手順を完了すると、次の継承の動作が発生します。  
  
-   デザイナーで、コントロールは、継承されたアイコンが表示されます。  
  
-   <xref:System.Windows.Forms.ToolStripPanel>コントロールがロックされている以外の場合は選択するか、その内容を再配置することはできません。  
  
-   コントロールを追加することができます、 <xref:System.Windows.Forms.ToolStripContentPanel>、コントロールを移動、およびそれらの子コントロールを作成、<xref:System.Windows.Forms.ToolStripContentPanel>です。  
  
-   フォームのビルド後、変更内容が永続化します。  
  
    > [!NOTE]
    >  すべてのアクセス修飾子を削除する<xref:System.Windows.Forms.ToolStripPanel>コントロールの一部である、<xref:System.Windows.Forms.ToolStripContainer>です。 アクセス修飾子、<xref:System.Windows.Forms.ToolStripContainer>コントロール全体を制御します。  
  
#### <a name="partial-trust"></a>部分信頼  
 制限事項`ToolStrip`s 部分信頼環境では許可されていない人物またはサービスで使用される個人情報の不慮のエントリを防ぐために設計されています。 保護措置は次のとおりです。  
  
-   `ToolStripDropDown` コントロールを必要と<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>内の項目を表示する、<xref:System.Windows.Forms.ToolStripControlHost>です。 これに適用されます両方の組み込みコントロールなど<xref:System.Windows.Forms.ToolStripTextBox>、 <xref:System.Windows.Forms.ToolStripComboBox>、および<xref:System.Windows.Forms.ToolStripProgressBar>ユーザーが作成したかも制御します。 この要件が満たされない場合、これらの項目は表示されません。 例外をスローすることはありません。  
  
-   設定、<xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A>プロパティを`false`は許可されていませんし、キャンセル可能な<xref:System.Windows.Forms.ToolStripDropDown.Closing>イベント パラメーターは無視されます。 ドロップダウンの項目を表示したまま 2 つ以上のキーストロークを入力できなくなります。 この要件が満たされない場合、このような項目は表示されません。 例外をスローすることはありません。  
  
-   以外の部分信頼のコンテキストで発生した場合、多くのキーストロークをイベントの処理は発生しません<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>です。  
  
-   アクセス キーがない場合に処理された<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>が許可されていません。  
  
#### <a name="usage"></a>使用法  
 次の使用パターンに関係がある<xref:System.Windows.Forms.ToolStrip>レイアウト、キーボード操作、およびエンドユーザーの動作。  
  
-   結合します。 <xref:System.Windows.Forms.ToolStripPanel>  
  
     <xref:System.Windows.Forms.ToolStrip>内で位置を変更できる、<xref:System.Windows.Forms.ToolStripPanel>および間で<xref:System.Windows.Forms.ToolStripPanel>s。 `Dock`プロパティは無視される場合、<xref:System.Windows.Forms.ToolStrip.Stretch%2A>プロパティは`false`では、サイズ、<xref:System.Windows.Forms.ToolStrip>に項目を追加するにつれて、<xref:System.Windows.Forms.ToolStripPanel>です。 通常、<xref:System.Windows.Forms.ToolStrip>タブ オーダーに関与しません。  
  
-   ドッキング  
  
     <xref:System.Windows.Forms.ToolStrip>固定位置にあるコンテナーの一方の側に配置し、ドッキングされている全体の端の上のサイズを拡張します。 通常、<xref:System.Windows.Forms.ToolStrip>タブ オーダーに関与しません。  
  
-   絶対位置  
  
     <xref:System.Windows.Forms.ToolStrip>他のコントロールと同様に、によって配置されているという点で、<xref:System.Windows.Forms.Control.Location%2A>プロパティがのサイズが固定されてし、通常、タブ オーダーに参加します。  
  
#### <a name="keyboard-interaction"></a>キーボードの相互作用  
  
##### <a name="access-keys"></a>アクセス キー  
 または、ALT キーと組み合わせることで、アクセス キーは、キーボードを使用してコントロールをアクティブ化する方法の 1 つです。 <xref:System.Windows.Forms.ToolStrip> 明示的および暗黙的なアクセス キーの両方をサポートしています。 明示的な定義は、アンパサンド (&) 文字、文字の前に使用します。 暗黙的に定義内の文字の順序に基づいて一致する項目を検索しようとするアルゴリズムを使用して、指定された`Text`プロパティです。  
  
##### <a name="shortcut-keys"></a>ショートカット キー  
 使用されるショートカット キー、<xref:System.Windows.Forms.MenuStrip>の組み合わせを使用して、<xref:System.Windows.Forms.Keys>列挙型 (注文固有ではない) ショートカット キーを定義します。 使用することも、 <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> "Delete"の代わりに"Del"を表示するなどのテキストのみのショートカット キーを表示するプロパティ  
  
##### <a name="navigation"></a>ナビゲーション  
 ALT キーをアクティブ化、<xref:System.Windows.Forms.MenuStrip>によって示される<xref:System.Windows.Forms.Form.MainMenuStrip%2A>です。 そこから、ctrl キーを押しながら TAB が移動する間<xref:System.Windows.Forms.ToolStrip>内で制御`ToolStripPanel`s。 内の項目間を移動する、TAB キーと、テンキーの方向キー、<xref:System.Windows.Forms.ToolStrip>です。 特殊なアルゴリズムは、オーバーフロー領域のナビゲーションを処理します。 Space キーを選択、 <xref:System.Windows.Forms.ToolStripButton>、 <xref:System.Windows.Forms.ToolStripDropDownButton>、または<xref:System.Windows.Forms.ToolStripSplitButton>です。  
  
##### <a name="focus-and-validation"></a>フォーカス イベントと検証  
 によって、ALT キーをアクティブ化されるときに、<xref:System.Windows.Forms.MenuStrip>または<xref:System.Windows.Forms.ToolStrip>をどちらも通常も、現在フォーカスがコントロールからフォーカスを削除します。 内でホストされるコントロールがあるかどうか、<xref:System.Windows.Forms.MenuStrip>またはのドロップダウン リスト、<xref:System.Windows.Forms.MenuStrip>ユーザーが TAB キーを押したときに、コントロールがフォーカスを取得します。 一般に、 <xref:System.Windows.Forms.Control.GotFocus>、 <xref:System.Windows.Forms.Control.LostFocus>、 <xref:System.Windows.Forms.Control.Enter>、および<xref:System.Windows.Forms.Control.Leave>のイベント<xref:System.Windows.Forms.MenuStrip>キーボードによってアクティブ化するときに発生しない可能性がします。 このような場合、使用して、<xref:System.Windows.Forms.MenuStrip.MenuActivate>と<xref:System.Windows.Forms.MenuStrip.MenuDeactivate>イベント代わりにします。  
  
 既定では、<xref:System.Windows.Forms.ToolStrip.CausesValidation%2A>は`false`します。 呼び出す<xref:System.Windows.Forms.ContainerControl.Validate%2A>検証を実行するフォームに明示的にします。  
  
#### <a name="layout"></a>レイアウト  
 制御する<xref:System.Windows.Forms.ToolStrip>のメンバーのいずれかを選択してレイアウト<xref:System.Windows.Forms.ToolStripLayoutStyle>で、<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>プロパティです。  
  
##### <a name="stack-layouts"></a>スタックのレイアウト  
 スタックの両端で互いの横にある項目の配置は、<xref:System.Windows.Forms.ToolStrip>です。 次の一覧では、スタックのレイアウトについて説明します。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow> が既定値です。 この設定により、<xref:System.Windows.Forms.ToolStrip>でに従ってで自動的にそのレイアウトを変更する、<xref:System.Windows.Forms.ToolStrip.Orientation%2A>プロパティをドラッグして、ドッキングのシナリオを処理します。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow> 表示、<xref:System.Windows.Forms.ToolStrip>互いの横にあるアイテムを垂直方向にします。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow> 表示、<xref:System.Windows.Forms.ToolStrip>水平方向の横にある他の項目。  
  
##### <a name="other-features-of-stack-layouts"></a>スタックのレイアウトの他の機能  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 最後の決定、<xref:System.Windows.Forms.ToolStrip>項目を揃えるためです。  
  
 ときに項目に収まらない場合、 <xref:System.Windows.Forms.ToolStrip>、オーバーフロー ボタンが自動的に表示されます。 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>プロパティの設定は、常に、必要に応じて、または never オーバーフロー領域に項目が表示されるかどうかを決定します。  
  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>イベントを調査できます、<xref:System.Windows.Forms.ToolStripItem.Placement%2A>項目がメイン上に配置するかどうかを決定するプロパティ<xref:System.Windows.Forms.ToolStrip>、オーバーフロー <xref:System.Windows.Forms.ToolStrip>、またはそれが現在表示されていないすべての場合。 項目が表示されない理由、一般的な原因としては、項目が、メインに収まらなかった<xref:System.Windows.Forms.ToolStrip>とその<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>プロパティに設定された<xref:System.Windows.Forms.ToolStripItemOverflow.Never>です。  
  
 ように、<xref:System.Windows.Forms.ToolStrip>に配置して移動可能な<xref:System.Windows.Forms.ToolStripPanel>と設定、<xref:System.Windows.Forms.ToolStrip.GripStyle%2A>に<xref:System.Windows.Forms.ToolStripGripStyle.Visible>です。  
  
##### <a name="other-layout-options"></a>その他のレイアウト オプション  
 その他のレイアウト オプションは<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>と<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>です。  
  
##### <a name="flow-layout"></a>フロー レイアウト  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> レイアウトの既定値は、 <xref:System.Windows.Forms.ContextMenuStrip>、 <xref:System.Windows.Forms.ToolStripDropDownMenu>、および<xref:System.Windows.Forms.ToolStripOverflow>です。 に似ていますが、<xref:System.Windows.Forms.FlowLayoutPanel>です。 機能<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>レイアウトを次に示します。  
  
-   すべての機能の<xref:System.Windows.Forms.FlowLayoutPanel>によって公開される、<xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>プロパティです。 キャストする必要があります、<xref:System.Windows.Forms.LayoutSettings>クラスを<xref:System.Windows.Forms.FlowLayoutSettings>クラスです。  
  
-   使用することができます、<xref:System.Windows.Forms.ToolStripItem.Dock%2A>と<xref:System.Windows.Forms.ToolStripItem.Anchor%2A>行内でアイテムを揃えるためのコードでのプロパティです。  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> プロパティは無視されます。  
  
-   <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>イベントを調査できます、<xref:System.Windows.Forms.ToolStripItem.Placement%2A>項目がメイン上に配置するかどうかを決定するプロパティ<xref:System.Windows.Forms.ToolStrip>収まりませんでしたか。  
  
-   ハンドルは、表示されませんし、そのため、<xref:System.Windows.Forms.ToolStrip>で<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>でレイアウト スタイル、<xref:System.Windows.Forms.ToolStripPanel>移動することはできません。  
  
-   <xref:System.Windows.Forms.ToolStrip>オーバーフロー ボタンは表示されず、および<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>は無視されます。  
  
##### <a name="table-layout"></a>テーブル レイアウト  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> レイアウトの既定値は、<xref:System.Windows.Forms.StatusStrip>です。 似ています<xref:System.Windows.Forms.TableLayoutPanel>です。 機能<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>レイアウトを次に示します。  
  
-   すべての機能の<xref:System.Windows.Forms.TableLayoutPanel>によって公開される、<xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>プロパティです。 キャストする必要があります、<xref:System.Windows.Forms.LayoutSettings>クラスを<xref:System.Windows.Forms.TableLayoutSettings>クラスです。  
  
-   使用することができます、<xref:System.Windows.Forms.ToolStripItem.Dock%2A>と<xref:System.Windows.Forms.ToolStripItem.Anchor%2A>テーブル セル内のアイテムを整列するコードでのプロパティです。  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> プロパティは無視されます。  
  
-   <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>イベントを調査できます、<xref:System.Windows.Forms.ToolStripItem.Placement%2A>項目がメイン上に配置するかどうかを決定するプロパティ<xref:System.Windows.Forms.ToolStrip>収まりませんでしたか。  
  
-   ハンドルは、表示されませんし、そのため、<xref:System.Windows.Forms.ToolStrip>で<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>でレイアウト スタイル、<xref:System.Windows.Forms.ToolStripPanel>移動することはできません。  
  
-   <xref:System.Windows.Forms.ToolStrip>オーバーフロー ボタンは表示されず、および<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>は無視されます。  
  
## <a name="toolstripitem"></a>ToolStripItem  
 次のトピックについて説明<xref:System.Windows.Forms.ToolStripItem>とそれから派生するコントロール。  
  
 <xref:System.Windows.Forms.ToolStripItem> すべての項目の抽象基本クラスには、<xref:System.Windows.Forms.ToolStrip>です。 次のオブジェクト モデルの表示、<xref:System.Windows.Forms.ToolStripItem>継承階層です。  
  
 ![ToolStripItem オブジェクト モデル](../../../../docs/framework/winforms/controls/media/toolstripitemobjectmodel.gif "ToolStripItemObjectModel")  
ToolStripItem オブジェクト モデル  
  
 <xref:System.Windows.Forms.ToolStripItem> クラスのいずれかからしか直接継承<xref:System.Windows.Forms.ToolStripItem>、ない直接の継承または<xref:System.Windows.Forms.ToolStripItem>を通じて<xref:System.Windows.Forms.ToolStripControlHost>または<xref:System.Windows.Forms.ToolStripDropDownItem>です。  
  
 <xref:System.Windows.Forms.ToolStripItem> コントロールに含まれる必要があります、 <xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.MenuStrip>、 <xref:System.Windows.Forms.StatusStrip>、または<xref:System.Windows.Forms.ContextMenuStrip>し、フォームに直接追加することはできません。 さまざまなコンテナー クラスが適切なサブセットを格納するように設計<xref:System.Windows.Forms.ToolStripItem>コントロール。  
  
 次の表に、在庫<xref:System.Windows.Forms.ToolStripItem>コントロールと検索最適なコンテナーです。 いずれかが<xref:System.Windows.Forms.ToolStrip>項目は、いずれかでホストできます<xref:System.Windows.Forms.ToolStrip>-コンテナー、派生したこれらの項目が、次のコンテナーで最適に表示するように設計されています。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown> デザイナーのツールボックスには表示されません。  
  
|含まれるアイテム|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|  
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|  
|<xref:System.Windows.Forms.ToolStripButton>|[はい]|いいえ|Ｘ|Ｘ|はい|  
|<xref:System.Windows.Forms.ToolStripComboBox>|はい|はい|はい|いいえ|はい|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|はい|いいえ|Ｘ|はい|はい|  
|<xref:System.Windows.Forms.ToolStripLabel>|はい|いいえ|Ｘ|はい|はい|  
|<xref:System.Windows.Forms.ToolStripSeparator>|はい|はい|はい|いいえ|はい|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|はい|いいえ|Ｘ|はい|はい|  
|<xref:System.Windows.Forms.ToolStripTextBox>|はい|はい|はい|いいえ|はい|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|いいえ|はい|はい|いいえ|Ｘ|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Ｘ|Ｘ|Ｘ|はい|いいえ|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|はい|いいえ|Ｘ|はい|いいえ|  
|<xref:System.Windows.Forms.ToolStripControlHost>|はい|はい|いいえ|はい|[はい]|  
  
### <a name="toolstripbutton"></a>ToolStripButton  
 <xref:System.Windows.Forms.ToolStripButton> ボタンの項目は、<xref:System.Windows.Forms.ToolStrip>です。 さまざまな境界線スタイルを表示して、表示および操作状態をアクティブ化を行うこともできます。 既定では、フォーカスがあるにも定義できます。  
  
### <a name="toolstriplabel"></a>ToolStripLabel  
 <xref:System.Windows.Forms.ToolStripLabel>ラベル機能を備えています<xref:System.Windows.Forms.ToolStrip>コントロール。 <xref:System.Windows.Forms.ToolStripLabel>に似ています、<xref:System.Windows.Forms.ToolStripButton>既定でフォーカスが移動されるしないと、プッシュまたは強調表示されたとしてレンダリングされません。  
  
 <xref:System.Windows.Forms.ToolStripLabel> ホストされている項目としては、アクセス キーをサポートしています。  
  
 使用して、 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>、 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>、および<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>プロパティを<xref:System.Windows.Forms.ToolStripLabel>でリンク コントロールをサポートするために、<xref:System.Windows.Forms.ToolStrip>です。  
  
### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel> バージョンは、<xref:System.Windows.Forms.ToolStripLabel>内使用専用に設計された<xref:System.Windows.Forms.StatusStrip>です。 特別な機能として<xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>、 <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>、および<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>です。  
  
### <a name="toolstripseparator"></a>ToolStripSeparator  
 <xref:System.Windows.Forms.ToolStripSeparator>ツールバーまたはメニューで、印刷の向きに応じてに垂直または水平方向の線を追加します。 グループ化やメニューなどのアイテムの違いを提供します。  
  
 追加することができます、<xref:System.Windows.Forms.ToolStripSeparator>ドロップダウン リストから選択してデザイン時にします。 ただし、ことができますも自動的に作成する、<xref:System.Windows.Forms.ToolStripSeparator>デザイナー テンプレート ノードまたはハイフン (-) を入力して、<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>メソッドです。  
  
### <a name="toolstripcontrolhost"></a>ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost> 抽象基本クラスは、 <xref:System.Windows.Forms.ToolStripComboBox>、 <xref:System.Windows.Forms.ToolStripTextBox>、および<xref:System.Windows.Forms.ToolStripProgressBar>です。 <xref:System.Windows.Forms.ToolStripControlHost> 2 つの方法で、カスタム コントロールを含む、他のコントロールをホストできます。  
  
-   構築、<xref:System.Windows.Forms.ToolStripControlHost>から派生するクラスと<xref:System.Windows.Forms.Control>です。 キャストする必要が完全にホストされるコントロールとプロパティにアクセスするには<xref:System.Windows.Forms.ToolStripControlHost.Control%2A>プロパティを実際にクラスを表します。  
  
-   拡張<xref:System.Windows.Forms.ToolStripControlHost>、継承されたクラスの既定のコンス トラクターで、基本クラス コンス トラクターの呼び出しから派生するクラスを渡すと<xref:System.Windows.Forms.Control>です。 このオプションで簡単にアクセスの一般的なコントロールのメソッドとプロパティをラップすることができます、<xref:System.Windows.Forms.ToolStrip>です。  
  
### <a name="toolstripcombobox"></a>ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox> <xref:System.Windows.Forms.ComboBox>でホストするために最適化された、<xref:System.Windows.Forms.ToolStrip>です。 ホストされるコントロールのプロパティとイベントのサブセットが公開されている、<xref:System.Windows.Forms.ToolStripComboBox>レベルが、基になる<xref:System.Windows.Forms.ComboBox>コントロールが完全にを介してアクセスできる、<xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A>プロパティです。  
  
### <a name="toolstriptextbox"></a>ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox> <xref:System.Windows.Forms.TextBox>でホストするために最適化された、<xref:System.Windows.Forms.ToolStrip>です。 ホストされるコントロールのプロパティとイベントのサブセットが公開されている、<xref:System.Windows.Forms.ToolStripTextBox>レベルが、基になる<xref:System.Windows.Forms.TextBox>コントロールが完全にを介してアクセスできる、<xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A>プロパティです。  
  
### <a name="toolstripprogressbar"></a>ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar> <xref:System.Windows.Forms.ProgressBar>でホストするために最適化された、<xref:System.Windows.Forms.ToolStrip>です。 ホストされるコントロールのプロパティとイベントのサブセットが公開されている、<xref:System.Windows.Forms.ToolStripProgressBar>レベルが、基になる<xref:System.Windows.Forms.ProgressBar>コントロールが完全にを介してアクセスできる、<xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A>プロパティです。  
  
### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem> 抽象基本クラスは、 <xref:System.Windows.Forms.ToolStripMenuItem>、 <xref:System.Windows.Forms.ToolStripDropDownButton>、および<xref:System.Windows.Forms.ToolStripSplitButton>項目を直接またはドロップダウン コンテナーのホスト項目をホストすることができます。 設定して、これを行う、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A>プロパティを<xref:System.Windows.Forms.ToolStripDropDown>と設定、<xref:System.Windows.Forms.ToolStrip.Items%2A>のプロパティ、<xref:System.Windows.Forms.ToolStripDropDown>です。 経由で直接これらドロップダウン項目へのアクセス、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A>プロパティです。  
  
### <a name="toolstripmenuitem"></a>ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem> <xref:System.Windows.Forms.ToolStripDropDownItem>と連動する<xref:System.Windows.Forms.ToolStripDropDownMenu>と<xref:System.Windows.Forms.ContextMenuStrip>をメニューの強調表示、レイアウト、および列の特別な構成を処理します。  
  
### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton> ようになります<xref:System.Windows.Forms.ToolStripButton>が、ユーザーがクリックしたときにドロップダウン領域を表示します。 設定して、ドロップダウン矢印を表示または非表示、<xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A>プロパティです。 <xref:System.Windows.Forms.ToolStripDropDownButton> ホスト、<xref:System.Windows.Forms.ToolStripOverflowButton>オーバーフローする項目を表示する、<xref:System.Windows.Forms.ToolStrip>です。  
  
### <a name="toolstripsplitbutton"></a>ToolStripSplitButton  
 <xref:System.Windows.Forms.ToolStripSplitButton> ボタンとドロップダウン ボタンの機能を結合します。  
  
 使用して、<xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A>同期するためにプロパティ、<xref:System.Windows.Forms.Control.Click>選択されたドロップダウン項目、ボタンに表示される項目のイベントです。  
  
### <a name="toolstripitem-generic-features"></a>ToolStripItem ジェネリックの機能  
 <xref:System.Windows.Forms.ToolStripItem> 次の一般的な機能とコントロールを継承するオプションを提供します。  
  
-   コア イベント  
  
-   イメージの処理  
  
-   アラインメント  
  
-   テキストとイメージの関係  
  
-   表示スタイル  
  
#### <a name="core-events"></a>コア イベント  
 <xref:System.Windows.Forms.ToolStripItem> コントロールは、自分をクリックして、マウス、および描画イベントを受信され、前処理もいくつかのキーボードを実行できます。  
  
#### <a name="image-handling"></a>イメージの処理  
 <xref:System.Windows.Forms.ToolStripItem.Image%2A>、 <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>、 <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>、 <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>、および<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A>プロパティは、イメージ処理のさまざまな側面に関連します。 内のイメージを使用して<xref:System.Windows.Forms.ToolStrip>コントロール直接これらのプロパティを設定するか、実行時間: 専用に設定して<xref:System.Windows.Forms.ToolStrip.ImageList%2A>プロパティです。  
  
 イメージのスケーリングは両方のプロパティの相互作用によって決まります<xref:System.Windows.Forms.ToolStrip>と<xref:System.Windows.Forms.ToolStripItem>、次のようにします。  
  
-   <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A> イメージの組み合わせによって決定される最終的なイメージの小数点以下桁数<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A>設定と、コンテナーの<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>設定します。  
  
    -   場合<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>は`true`(既定) と<xref:System.Windows.Forms.ToolStripItemImageScaling>は<xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>、イメージのスケーリングは行われません、および<xref:System.Windows.Forms.ToolStrip>サイズが最大のアイテム、または指定された最小サイズのです。  
  
    -   場合<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>は`false`と<xref:System.Windows.Forms.ToolStripItemImageScaling>は<xref:System.Windows.Forms.ToolStripItemImageScaling.None>、どちらのイメージも<xref:System.Windows.Forms.ToolStrip>スケーリングが発生します。  
  
#### <a name="alignment"></a>アラインメント  
 値、<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>プロパティの末尾を決定する、<xref:System.Windows.Forms.ToolStrip>で項目が表示されます。 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A>プロパティは場合にのみ、機能のレイアウト スタイル、<xref:System.Windows.Forms.ToolStrip>スタック オーバーフローの値のいずれかに設定されています。  
  
 項目を配置している、<xref:System.Windows.Forms.ToolStrip>項目のコレクション内の項目が表示される順序で。 項目のレイアウト位置をプログラムで変更するには、使用、<xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A>コレクション内のアイテムの移動メソッドです。 このメソッドは、項目を移動が、複製はしません。  
  
#### <a name="text-and-image-relationship"></a>テキストとイメージのリレーションシップ  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>プロパティのテキストに対して、画像の相対的な位置を定義する、<xref:System.Windows.Forms.ToolStripItem>です。 イメージ、テキスト、またはその両方が不足しているアイテムの特殊なケースとして扱われますできるように、<xref:System.Windows.Forms.ToolStripItem>不足している要素または要素の空の部分は表示されません。  
  
#### <a name="display-style"></a>表示スタイル  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 目的のみを表示するときに、アイテムのテキストおよびイメージのプロパティの値を設定できます。 これは通常、表示スタイルのみを変更する、さまざまなコンテキストで同じ項目を表示する場合に使用されます。  
  
## <a name="accessory-classes"></a>アクセサリ クラス  
 さまざまな他の機能を提供するクラスは次のとおりです。  
  
-   <xref:System.Windows.Forms.ToolStripManager> サポートしている<xref:System.Windows.Forms.ToolStrip>-全体のアプリケーション、マージ、設定、およびレンダラー オプションなどのタスクに関連します。  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> 特定のスタイルやテーマを適用することができます、<xref:System.Windows.Forms.ToolStrip>簡単にします。  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> ペンと置き換え可能なカラー テーブルに基づくブラシを作成 (<xref:System.Windows.Forms.ProfessionalColorTable>)。  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> システム カラーとフラット visual スタイルを適用<xref:System.Windows.Forms.ToolStrip>アプリケーションです。  
  
-   <xref:System.Windows.Forms.ToolStripContainer> ような<xref:System.Windows.Forms.SplitContainer>します。 4 つの側のドッキングされたパネルを使用して (インスタンスの<xref:System.Windows.Forms.ToolStripPanel>) と 1 つの中央パネル (のインスタンス<xref:System.Windows.Forms.ToolStripContentPanel>) 標準的な並べ替え方法を作成します。 サイド パネルを削除することはできませんが、非表示にすることができます。 削除も、中央のパネルを非表示にします。 1 つまたは複数を配置して<xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.MenuStrip>、または<xref:System.Windows.Forms.StatusStrip>側パネルのコントロールは、その他のコントロールの中央のパネルを使用できます。 <xref:System.Windows.Forms.ToolStripContentPanel>一貫した外観にフォームの本文をサポートするレンダラーを取得する方法も提供します。 <xref:System.Windows.Forms.ToolStripContainer> マルチ ドキュメント インターフェイス (MDI) はサポートされません。  
  
-   <xref:System.Windows.Forms.ToolStripPanel> 移動および配置するための領域を提供<xref:System.Windows.Forms.ToolStrip>コントロール。 1 つだけのパネルを使用するには、これを選択した場合と<xref:System.Windows.Forms.ToolStripPanel>は MDI のシナリオに適しています。  
  
## <a name="see-also"></a>関連項目  
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)  
 [ToolStrip コントロール](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [MenuStrip コントロール](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [StatusStrip コントロール](../../../../docs/framework/winforms/controls/statusstrip-control.md)  
 [ContextMenuStrip コントロール](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)  
 [BindingNavigator コントロール](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
