---
title: '方法 : ContextMenuOpening イベントを処理する'
ms.date: 03/30/2017
helpviewer_keywords:
- ContextMenuOpening properties [WPF]
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
ms.openlocfilehash: ab4c4867981cd318738b7404d76f2f5932bb9059
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547486"
---
# <a name="how-to-handle-the-contextmenuopening-event"></a>方法 : ContextMenuOpening イベントを処理する
<xref:System.Windows.FrameworkElement.ContextMenuOpening>か、既存のコンテキスト メニューの前、表示するかを抑制する状況を設定して表示されるメニューを調整するアプリケーションでイベントを処理することができます、<xref:System.Windows.RoutedEventArgs.Handled%2A>プロパティを`true`イベント データ。 設定の一般的な理由<xref:System.Windows.RoutedEventArgs.Handled%2A>に`true`データが完全に新しいメニューを置き換えるには、イベントの<xref:System.Windows.Controls.ContextMenu>オブジェクトの操作を取り消すと、新しいオープンを開始も必要があります。 ハンドラーを記述する場合、<xref:System.Windows.FrameworkElement.ContextMenuOpening>イベント、する必要がありますの間のタイミングの問題に注意してください、<xref:System.Windows.Controls.ContextMenu>コントロールとサービスが開くと、一般にコントロールのコンテキスト メニューの位置を担当します。 このトピックでは、コンテキスト メニューのさまざまなシナリオを開くためのコードの手法の一部を示していて、タイミングの問題が関係する状況を示しています。  
  
 処理するためのいくつかのシナリオ、<xref:System.Windows.FrameworkElement.ContextMenuOpening>イベント。  
  
-   表示される前に、メニュー項目を調整します。  
  
-   表示される前に、[全体] メニューを置換します。  
  
-   完全に既存のどのコンテキスト メニューを抑制して、コンテキスト メニューが表示されません。  
  
## <a name="example"></a>例  
  
## <a name="adjusting-the-menu-items-before-display"></a>表示される前に、メニュー項目を調整します。  
 既存のメニュー項目を調整することは非常に単純なであり、最も一般的なシナリオで、可能性があります。 追加またはアプリケーションの現在の状態情報や、コンテキスト メニューが要求されたオブジェクトのプロパティとして使用できる特定の状態情報への応答のコンテキスト メニュー オプションを減算するためにこれを行う場合があります。  
  
 一般的な手法を右クリックされた特定のコントロールである、イベントのソースを取得し、取得、<xref:System.Windows.FrameworkElement.ContextMenu%2A>からプロパティです。 チェックする通常、<xref:System.Windows.Controls.ItemsControl.Items%2A>既にメニューで、存在し、追加または削除適切な新しいコンテキスト メニュー項目を表示するコレクション<xref:System.Windows.Controls.MenuItem>にまたはコレクションから項目。  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## <a name="replacing-the-entire-menu-before-display"></a>表示される前にメニュー全体を置き換える  
 代替のシナリオは、コンテキスト メニュー全体を置換するかどうかです。 使用すること言うまでも上記のコードでのバリエーションを既存のコンテキスト メニューのすべての項目を削除し、項目の 0 から始まる新しい列を追加します。 新規作成には、コンテキスト メニューのすべての項目を置換するためより直感的なアプローチが<xref:System.Windows.Controls.ContextMenu>項目では、設定、設定して、<xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>に新しいコントロールのプロパティの<xref:System.Windows.Controls.ContextMenu>します。  
  
 置換するための単純なハンドラー コードを次に示します、<xref:System.Windows.Controls.ContextMenu>です。 このコードでカスタム参照`BuildMenu`分離されているために呼び出されます例ハンドラーの 1 つ以上メソッドです。  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 ただし、イベントのハンドラーのこのスタイルを使用する場合<xref:System.Windows.FrameworkElement.ContextMenuOpening>場合、タイミングの問題をしまう可能性があります設定しているオブジェクト、<xref:System.Windows.Controls.ContextMenu>既存のコンテキスト メニューはありません。 ユーザーが、コントロールを右クリックしたときに<xref:System.Windows.FrameworkElement.ContextMenuOpening>が発生した場合でも、既存<xref:System.Windows.Controls.ContextMenu>が空または null。 ここでは、任意の新しい<xref:System.Windows.Controls.ContextMenu>ソースに設定する要素は、表示される遅すぎますが到着するとします。 また、な場合は、ユーザーをもう一度右クリックし、今回の新しい<xref:System.Windows.Controls.ContextMenu>が表示されたら、値が null でないと、ハンドラーが正しく置換され、ハンドラーを 2 回目の実行時にメニューを表示します。 これは、2 つの方法を示しています。  
  
1.  保証を<xref:System.Windows.FrameworkElement.ContextMenuOpening>ハンドラーが常に、少なくとも、プレース ホルダーを持つコントロールに対して実行<xref:System.Windows.Controls.ContextMenu>、使用可能なハンドラー コードによって置き換えられる対象です。 ここでは、前の例に示すようにハンドラーを使用することもできますが、通常のプレース ホルダーを指定する<xref:System.Windows.Controls.ContextMenu>初期のマークアップで。  
  
     [!code-xaml[ContextMenuOpeningHandlers#XAMLWithInitCM](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2.  あると想定初期<xref:System.Windows.Controls.ContextMenu>値が null で、いくつかの予備のロジックに基づきます。 いずれかのチェック方法があります。<xref:System.Windows.Controls.ContextMenu>を少なくとも 1 回の null の場合、または、コード、ハンドラーが解除されているかどうかにフラグを使用して実行します。 あると想定するため、<xref:System.Windows.Controls.ContextMenu>に表示される、ハンドラーについては、設定<xref:System.Windows.RoutedEventArgs.Handled%2A>に`true`イベント データ。 <xref:System.Windows.Controls.ContextMenuService>コンテキスト メニューの表示を担当する、`true`値<xref:System.Windows.RoutedEventArgs.Handled%2A>イベントのデータが、コンテキスト メニューの表示を取り消す/イベントを発生させたの組み合わせを制御する要求を表します。  
  
 次の手順が、新しいものを指定するは、可能性のある問題のあるコンテキスト メニューを抑制したが、これで、それを表示します。 1 つは、基本的に前のハンドラーと同じ新しい設定: 新しいをビルドする<xref:System.Windows.Controls.ContextMenu>コントロールのソースを設定および<xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>関連付けのプロパティです。 最初の試行を抑制するために、追加の手順は、コンテキスト メニューの表示を今すぐ強制的する必要がありますです。 設定するには、表示、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=nameWithType>プロパティを`true`ハンドラー内にします。 注意してこれを行うときに発生、ハンドラーのコンテキスト メニューを開くため、<xref:System.Windows.FrameworkElement.ContextMenuOpening>イベントをもう一度です。 ハンドラーを再入力する場合、それが再帰的なである無限になります。 これは、常に確認する必要がある理由`null`内からコンテキスト メニューを開く場合は、フラグを使用して、または、<xref:System.Windows.FrameworkElement.ContextMenuOpening>イベント ハンドラー。  
  
## <a name="suppressing-any-existing-context-menu-and-displaying-no-context-menu"></a>既存のどのコンテキスト メニューを抑制して、コンテキスト メニューが表示されません。  
 最後のシナリオでは、完全には、メニューを抑制するハンドラーの記述は一般的ではありません。 場合は、指定されたコントロールは、コンテキスト メニューを表示することはできませんは、これよりも、ユーザーが要求するときにだけに、メニューを抑制することを確実にする可能性がありますより適切な方法があります。 コンテキスト メニューを抑制して、何も表示するハンドラーを使用するかどうかは、単に、ハンドラーを設定する必要がありますが、<xref:System.Windows.RoutedEventArgs.Handled%2A>に`true`イベント データ。 <xref:System.Windows.Controls.ContextMenuService>をに対しては責任をコンテキスト メニューを表示するは、コントロールで発生したイベントのイベント データを確認します。 イベントが設定されていた場合<xref:System.Windows.RoutedEventArgs.Handled%2A>任意の場所、ルートし、イベントを開始したコンテキスト メニュー開いているアクションを非表示にします。  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>  
 [基本要素の概要](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [ContextMenu の概要](../../../../docs/framework/wpf/controls/contextmenu-overview.md)
