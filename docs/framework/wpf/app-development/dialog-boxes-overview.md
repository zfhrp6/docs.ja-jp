---
title: "ダイアログ ボックスの概要"
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
- modeless dialog boxes [WPF]
- dialog boxes [WPF]
- message boxes [WPF]
- modal dialog boxes [WPF]
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 112a9badaf9a64b2c6d3f73d64c27fbc36ec48a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="dialog-boxes-overview"></a>ダイアログ ボックスの概要
スタンドアロン アプリケーションは通常、メイン ウィンドウが対象で、アプリケーションが動作して、を介してそのデータを処理する機能を公開、メイン データをある[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]メカニズムは、メニュー バー、ツールバー、およびステータス バーと同様にします。 重要なアプリケーションは、次のようなことをするための追加のウィンドウを表示することもあります。  
  
-   固有の情報をユーザーに表示する。  
  
-   ユーザーから情報を収集する。  
  
-   情報の表示と収集の両方を行う。  
  
 これらの種類のウィンドウと呼ばれる *ダイアログ ボックス*、し、2 種類があります: モーダルとモードレスです。  
  
 A*モーダル*関数には、引き続きユーザーからの追加データが必要がある場合、関数によってダイアログ ボックスが表示されます。 機能は、モーダル ダイアログ ボックスに依存してデータを収集するため、モーダル ダイアログ ボックスが開いている間、ユーザーはアプリケーション内の他のウィンドウをアクティブ化することはできません。 ほとんどの場合、モーダル ダイアログ ボックスで、ユーザー キーを押して、モーダル ダイアログ ボックスを終了する場合はシグナルを**OK**または**キャンセル**ボタンをクリックします。 キーを押して、 **OK**ボタンは、こと、ユーザーがデータを入力し、データ処理を継続する関数を示します。 キーを押して、**キャンセル**ボタンは、ユーザーが、関数が完全に実行を停止することを示します。 モーダル ダイアログ ボックスの最も一般的な例は、データを開く、保存する、および印刷するために表示されます。  
  
 A*モードレス*ダイアログ ボックスで、その一方は防止しません、ユーザーが開いている間、他のウィンドウをアクティブ化します。 たとえば、ユーザーがドキュメント内の特定の単語の出現箇所を検索する場合、メイン ウィンドウは、多くの場合、ダイアログ ボックスを開いて、検索する単語をユーザーに尋ねます。 しかし、単語の検索中もユーザーはドキュメントを編集できるため、ダイアログ ボックスがモーダルである必要はありません。 モードレス ダイアログ ボックスは、少なくとも、**閉じる** ダイアログ ボックスを閉じるボタンをクリックしなどの特定の機能を実行するその他のボタンを提供する場合があります、**次を検索**ボタン、次へ を検索する単語が単語の検索の検索条件に一致します。  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] では、メッセージ ボックス、コモン ダイアログ ボックス、カスタム ダイアログ ボックスなど、いくつかの種類のダイアログ ボックスを作成できます。 このトピックでは、それぞれ、[ダイアログ ボックスのサンプル](http://go.microsoft.com/fwlink/?LinkID=159984)一致する例を示します。  
  
 
  
<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>メッセージ ボックス  
 A*メッセージ ボックス*テキストの情報を表示し、ボタンを持つ意思決定を行うようにするために使用できるダイアログ ボックスです。 次の図は、テキスト情報と質問を表示して、ユーザーが質問に回答するための 3 つのボタンを表示するメッセージ ボックスを示しています。  
  
 ![[Word Processor] ダイアログ ボックス](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure1.png "DialogBoxesOverviewFigure1")  
  
 使用するメッセージ ボックスを作成する、<xref:System.Windows.MessageBox>クラスです。 <xref:System.Windows.MessageBox>メッセージ ボックスのテキスト、タイトル、アイコン、およびボタンは、次のようにコードを使用して構成することができます。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 表示するには、メッセージ ボックスを呼び出す、 `static` <xref:System.Windows.MessageBox.Show%2A>メソッドを次のコードに示すようにします。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 メッセージ ボックスを表示するコードで、ユーザーの決定 (どのボタンが押されたか) を検出して処理する必要があるときには、コードは、次のコードに示されているように、メッセージ ボックスの結果を検査できます。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 メッセージ ボックスの使用の詳細については、次を参照してください。 <xref:System.Windows.MessageBox>、 [MessageBox サンプル](http://go.microsoft.com/fwlink/?LinkID=160023)、および[ダイアログ ボックスのサンプル](http://go.microsoft.com/fwlink/?LinkID=159984)です。  
  
 <xref:System.Windows.MessageBox>単純なダイアログ ボックス ユーザー エクスペリエンスを使用する利点を提供することがあります<xref:System.Windows.MessageBox>部分信頼セキュリティ サンド ボックス内で実行されるアプリケーションで表示できるウィンドウの唯一の型では、(を参照してください[セキュリティ](../../../../docs/framework/wpf/security-wpf.md)) など[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]です。  
  
 ほとんどのダイアログ ボックスは、テキスト、選択 (チェック ボックス)、相互に排他的な選択 (オプション ボタン)、リスト選択 (リスト ボックス、コンボ ボックス、ドロップダウン リスト ボックス) など、メッセージ ボックスの結果よりも複雑なデータを表示し、収集します。 これらのオプション、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]いくつかの一般的なダイアログ ボックスを提供し、いずれかの使用は完全信頼で実行されているアプリケーションに限定されますが、独自のダイアログ ボックスを作成することができます。  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>コモン ダイアログ ボックス  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] は、ファイルを開く、ファイルを保存する、印刷するためのダイアログ ボックスなど、すべてのアプリケーションに共通の、さまざまな再利用可能なダイアログ ボックスを実装します。 これらのダイアログ ボックスはオペレーティング システムによって実装されるため、そのオペレーティング システム上で実行するすべてのアプリケーション間で共有でき、ユーザー エクスペリエンスの一貫性を保つことができます。ユーザーが 1 つのアプリケーションで、オペレーティング システムによって提供されるダイアログ ボックスの使用に慣れると、他のアプリケーションでも、そのダイアログ ボックスの使用法を学ぶ必要はありません。 これらのダイアログ ボックスはすべてのアプリケーションで使用され、一貫性のあるユーザー エクスペリエンスを提供するのに役立つ、ために、それらと呼ばれます。*コモン ダイアログ ボックス*です。  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] は、ファイルを開く、ファイルを保存する、および印刷コモン ダイアログ ボックスをカプセル化して、スタンドアロン アプリケーションで使用できるマネージ クラスとして公開します。 このトピックでは、それぞれの概要を簡単に説明します。  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>[ファイルを開く] ダイアログ ボックス  
 [ファイルを開く] ダイアログ ボックスは、次の図に示されているように、開くファイルの名前を取得するために、ファイルを開く機能によって使用されます。  
  
 ![[開く] ダイアログ ボックス](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure2.png "DialogBoxesOverviewFigure2")  
  
 一般的なファイルを開く ダイアログ ボックスとして実装されている、<xref:Microsoft.Win32.OpenFileDialog>クラスし、内にある、<xref:Microsoft.Win32>名前空間。 次のコードは、[ファイルを開く] ダイアログ ボックスの作成、構成、および表示の方法と、結果を処理する方法を示しています。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 ファイルを開く ダイアログ ボックスの詳細については、次を参照してください。<xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>です。  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog>ファイル名を安全に取得する部分的な信頼で実行されているアプリケーションで使用できます (を参照してください[セキュリティ](../../../../docs/framework/wpf/security-wpf.md))。  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>[ファイルの保存] ダイアログ ボックス  
 [ファイルの保存] ダイアログ ボックスは、次の図に示されているように、保存するファイルの名前を取得するために、ファイルを保存する機能によって使用されます。  
  
 ![[名前を付けて保存] ダイアログ ボックス](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure3.png "DialogBoxesOverviewFigure3")  
  
 一般的な保存ファイル ダイアログ ボックスとして実装、<xref:Microsoft.Win32.SaveFileDialog>クラス、および内にある、<xref:Microsoft.Win32>名前空間。 次のコードは、[ファイルを開く] ダイアログ ボックスの作成、構成、および表示の方法と、結果を処理する方法を示しています。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 保存の詳細については [ファイル] ダイアログ ボックスを参照してください<xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>です。  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>[印刷] ダイアログ ボックス  
 次の図に示されているように、[印刷] ダイアログ ボックスは、ユーザーがデータを印刷するプリンターを選択し、構成するために、印刷機能によって使用されます。  
  
 ![[印刷] ダイアログ ボックス](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure4.png "DialogBoxesOverviewFigure4")  
  
 一般的な印刷ダイアログ ボックスは、<xref:System.Windows.Controls.PrintDialog>クラス、および内にある、<xref:System.Windows.Controls>名前空間。 次のコードは、[印刷] ダイアログ ボックスの作成、構成、および表示の方法を示しています。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 詳細については、[印刷] ダイアログ ボックスで、次を参照してください。<xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>です。 印刷の詳細については[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]を参照してください[印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)です。  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>カスタム ダイアログ ボックス  
 コモン ダイアログ ボックスは便利であり、可能なときにはコモン ダイアログ ボックスを使用する必要がありますが、ドメイン固有のダイアログ ボックスの要件はサポートしていません。 このような場合は、独自のダイアログ ボックスを作成する必要があります。 これから説明するように、ダイアログ ボックスは、特殊な動作を持つウィンドウです。 <xref:System.Windows.Window>これらの動作を実装して、その結果を使用する<xref:System.Windows.Window>カスタム モーダルとモードレスのダイアログ ボックスを作成します。  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>モーダルのカスタム ダイアログ ボックスの作成  
 このトピックは、使用する方法を示します<xref:System.Windows.Window>、通常のモーダル ダイアログ ボックスの実装を作成するを使用して、`Margins`例として、ダイアログ ボックス (を参照してください[ダイアログ ボックスのサンプル](http://go.microsoft.com/fwlink/?LinkID=159984))。 `Margins`  ダイアログ ボックスが次の図に示すようにします。  
  
 ![[余白] ダイアログ ボックス](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure5.png "DialogBoxesOverviewFigure5")  
  
#### <a name="configuring-a-modal-dialog-box"></a>モーダル ダイアログ ボックスの構成  
 一般的なダイアログ ボックスのユーザー インターフェイスには、次の項目が含まれます。  
  
-   必要なデータを収集するために必要なさまざまなコントロール。  
  
-   表示、 **OK**ボタン ユーザーがクリックすると、関数に戻り、ダイアログ ボックスを閉じるし、処理を続行します。  
  
-   表示、**キャンセル** ダイアログ ボックスを閉じるし、関数の処理を停止するユーザーがクリックしたボタンをクリックします。  
  
-   表示、**閉じる**タイトル バーのボタンをクリックします。  
  
-   アイコンの表示。  
  
-   表示**最小化**、**最大化**、および**復元**ボタン。  
  
-   表示、**システム**メニューを最小限に抑える、最大化、復元、およびダイアログ ボックスを閉じます。  
  
-   ダイアログ ボックスは、ダイアログ ボックスを開いたウィンドウの上と中央に開きます。  
  
-   ダイアログ ボックスは、可能な場合はサイズ変更可能である必要があるため、ダイアログ ボックスが小さくなりすぎるのを避け、便利な既定サイズをユーザーに提供するために、既定の寸法と最小寸法の両方を設定する必要があります。  
  
-   原因となるショートカットとして構成する必要があります、ESC キーを押して、**キャンセル** ボタンを押します。 これを実現するには、<xref:System.Windows.Controls.Button.IsCancel%2A>のプロパティ、**キャンセル** ボタンをクリックして`true`です。  
  
-   原因となるショートカットとして構成する必要がありますを入力してください (または戻り値) のキーを押して、 **OK**  ボタンを押します。 これを実現するには、<xref:System.Windows.Controls.Button.IsDefault%2A>のプロパティ、 **OK**ボタン`true`です。  
  
 次のコードは、この構成の例を示しています。  
  
 [!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup2)]  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind2)]  
  
 ダイアログ ボックスのユーザー エクスペリエンスは、ダイアログ ボックスを開くウィンドウのメニュー バーにも及びます。 メニュー項目が、機能の続行には、ダイアログ ボックスでのユーザーの操作を必要とする機能を実行するときには、次に示されているように、その機能のメニュー項目の見出しに省略記号を付けます。  
  
 [!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup1)]  
[!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup2)]  
  
 メニュー項目が、[バージョン情報] ダイアログ ボックスなど、ユーザーの操作を必要としないダイアログ ボックスを表示する機能を実行するときには、省略記号は必要ありません。  
  
#### <a name="opening-a-modal-dialog-box"></a>モーダル ダイアログ ボックスを開く  
 ダイアログ ボックスは、通常、ワード プロセッサでドキュメントの余白を設定するなど、ドメイン固有の機能を実行するためにユーザーがメニュー項目を選択した結果として表示されます。 ウィンドウをダイアログ ボックスとして表示するのは、通常のウィンドウを表示するのと同様ですが、ダイアログ ボックス固有の追加の構成が必要です。 ダイアログ ボックスのインスタンス化、構成、および開くプロセスの全体を、次のコードに示します。  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind4)]  
  
 ここでは、コードは、既定の情報 (現在の余白) をダイアログ ボックスに渡しています。 設定されるも、 <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType>  ダイアログ ボックスが表示されているウィンドウへの参照を持つプロパティです。 一般に、必ず設定してすべてのダイアログ ボックスに共通するウィンドウの状態関連の動作を提供する ダイアログ ボックスの所有者 (を参照してください[WPF Windows 概要](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)詳細については)。  
  
> [!NOTE]
>  サポートするために所有者を指定する必要があります[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ダイアログ ボックスのオートメーション (を参照してください[UI オートメーションの概要](../../../../docs/framework/ui-automation/ui-automation-overview.md))。  
  
 呼び出しでモーダルとして表示されます ダイアログ ボックスを構成した後、<xref:System.Windows.Window.ShowDialog%2A>メソッドです。  
  
#### <a name="validating-user-provided-data"></a>ユーザー指定データの検証  
 ダイアログ ボックスが開かれ、ユーザーが必要なデータを指定すると、ダイアログ ボックスは、指定されたデータが有効であることを確認する必要があります。これは、次のような理由からです。  
  
-   セキュリティの観点から、すべての入力を検証する必要があります。  
  
-   ドメイン固有の観点から、データの検証は、誤ったデータがコードによって処理されて、例外がスローされるのを防ぎます。  
  
-   ユーザー エクスペリエンスの観点から、ダイアログ ボックスは、入力したデータが無効であることを示すことによって、ユーザーを支援できます。  
  
-   パフォーマンスの観点から、多層アプリケーションでのデータの検証は、特に、アプリケーションが Web サービスまたはサーバーベースのデータベースで構成される場合、クライアント層とアプリケーション層の間のラウンド トリップの回数を減らすことができます。  
  
 バインドされたコントロールを検証する[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、検証規則を定義し、バインドに関連付ける必要があります。 検証規則はから派生するカスタム クラス<xref:System.Windows.Controls.ValidationRule>です。 次の例では、検証規則、 `MarginValidationRule`、バインドされた値は、どのチェック、<xref:System.Double>と指定された範囲内にあります。  
  
 [!code-csharp[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs#marginvalidationrulecode)]
 [!code-vb[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb#marginvalidationrulecode)]  
  
 オーバーライドすることでこのコードで、検証規則の検証ロジックが実装されている、<xref:System.Windows.Controls.ValidationRule.Validate%2A>メソッドでは、データを検証し、適切な返します<xref:System.Windows.Controls.ValidationResult>です。  
  
 検証規則をバインド コントロールに関連付けるには、次のマークアップを使用します。  
  
 [!code-xaml[DialogBoxSample#MarginsValidationMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup2)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup3)]  
  
 検証規則が関連付けられている[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]自動的に適用されますが、バインドされたコントロールにデータが入力されるとします。 コントロールには、無効なデータが含まれている[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]次の図に示すように、無効なコントロール周囲に赤い境界線が表示されます。  
  
 ![無効な左余白](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure7.png "DialogBoxesOverviewFigure7")  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、ユーザーが有効なデータを入力するまで、ユーザーを無効なコントロールに制限するわけではありません。 これは、ダイアログ ボックスとして適切な動作です。データが有効かどうかにかかわらず、ユーザーはダイアログ ボックス内のコントロールを自由に移動できる必要があります。 ただし、これは、無効なデータとキーを押して、ユーザーが入力、 **OK**ボタンをクリックします。 このため、コードも必要があるダイアログ内のすべてのコントロールを検証するときにボックス、 **[ok]**ボタンを処理することにより、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind3)]  
  
 このコードは、ウィンドウ上のすべての依存関係オブジェクトを列挙し、いずれかが有効ではない場合 (によって返される<xref:System.Windows.Controls.Validation.GetHasError%2A>、無効なコントロールがフォーカスを取得、`IsValid`メソッドを返します。 `false`、ウィンドウは無効とみなされるとします。  
  
 ダイアログ ボックスが有効な場合は、安全に閉じて、戻ることができます。 復帰プロセスの一環として、呼び出し元の機能に結果を返す必要があります。  
  
#### <a name="setting-the-modal-dialog-result"></a>モーダル ダイアログ ボックスの結果を設定する  
 使用してダイアログ ボックスを開く<xref:System.Windows.Window.ShowDialog%2A>メソッドを呼び出す場合と基本的には: コードを使用して、ダイアログ ボックスを開いた<xref:System.Windows.Window.ShowDialog%2A>までを待ちます<xref:System.Windows.Window.ShowDialog%2A>を返します。 ときに<xref:System.Windows.Window.ShowDialog%2A>を返します、呼び出し元のコードが必要かどうかに基づくした処理を続行するか、処理を停止するかどうかを決定する場合は、ユーザーが押された、 **[ok]**ボタンまたは**キャンセル**ボタンをクリックします。 としてユーザーの選択を返す必要があります ダイアログ ボックスをこの決定を容易にする、<xref:System.Boolean>から返される値、<xref:System.Windows.Window.ShowDialog%2A>メソッドです。  
  
 ときに、 **OK**ボタンをクリックすると、<xref:System.Windows.Window.ShowDialog%2A>返す必要があります`true`です。 これを実現するには、<xref:System.Windows.Window.DialogResult%2A>プロパティ ダイアログ ボックスのボックス、 **[ok]**ボタンをクリックします。  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind3)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind4)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind4)]  
  
 その設定に注意してください、<xref:System.Windows.Window.DialogResult%2A>プロパティを明示的に呼び出す必要性が軽減されるウィンドウを自動的に閉じるをによりも<xref:System.Windows.Window.Close%2A>します。  
  
 ときに、**キャンセル**ボタンをクリックすると、<xref:System.Windows.Window.ShowDialog%2A>返す必要があります`false`の設定も必要があります、<xref:System.Windows.Window.DialogResult%2A>プロパティです。  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind3)]  
  
 ときに、ボタンの<xref:System.Windows.Controls.Button.IsCancel%2A>プロパティに設定されている`true`いずれかを押すと、**キャンセル**ボタンまたは ESC キー<xref:System.Windows.Window.DialogResult%2A>に自動的に設定されている`false`です。 次のマークアップが上記のコードで処理する必要がない場合と同様、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
 [!code-xaml[DialogBoxSample#MarginsDialogDefaultCancelMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogdefaultcancelmarkup)]  
  
 ダイアログ ボックスが自動的に返します`false`、ユーザーが押したとき、**閉じる**タイトル バー ボタンをクリックするか、**閉じる**からメニュー項目、**システム**メニュー。  
  
#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>モーダル ダイアログ ボックスから返されたデータの処理  
 ときに<xref:System.Windows.Window.DialogResult%2A>設定されているダイアログ ボックスでは、によって開いたとき、関数は、検査することによってダイアログ ボックスの結果を取得できます、<xref:System.Windows.Window.DialogResult%2A>プロパティと<xref:System.Windows.Window.ShowDialog%2A>を返します。  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind4)]  
  
 ダイアログの結果が場合`true`、関数として使用するキューを取得して、ユーザーによって提供されるデータを処理します。  
  
> [!NOTE]
>  後に<xref:System.Windows.Window.ShowDialog%2A>が返されると、ダイアログ ボックスを再度開くことはできません。 代わりに、新しいインスタンスを作成する必要があります。  
  
 ダイアログの結果が場合`false`関数が適切に処理を終了する必要があります。  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>モードレス カスタム ダイアログ ボックスの作成  
 次の図に示されている [検索] ダイアログ ボックスなどのモードレス ダイアログ ボックスは、基本的な外観はモーダル ダイアログ ボックスと同じです。  
  
 ![[検索] ダイアログ ボックス](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure6.PNG "DialogBoxesOverviewFigure6")  
  
 しかし、次のセクションで説明するように、動作は少し異なります。  
  
#### <a name="opening-a-modeless-dialog-box"></a>モードレス ダイアログ ボックスを開く  
 呼び出すことによって、モードレス ダイアログ ボックスが開かれ、<xref:System.Windows.Window.Show%2A>メソッドです。  
  
 [!code-xaml[DialogBoxSample#OpenFindDialogMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#openfinddialogmarkup1)]  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind3)]  
  
 異なり<xref:System.Windows.Window.ShowDialog%2A>、<xref:System.Windows.Window.Show%2A>が直ちに返されます。 その結果、呼び出し元のウィンドウは、モードレス ダイアログ ボックスが閉じられたことを知ることができず、したがって、ダイアログ ボックスの結果を確認するタイミングを判断したり、ダイアログ ボックスからデータを取得して、さらに処理したりすることができません。 代わりに、ダイアログ ボックスは、別の方法を作成して、呼び出し元のウィンドウに処理用のデータを返す必要があります。  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>モードレス ダイアログ ボックスから返されたデータの処理  
 この例では、 `FindDialogBox` 1 つまたは複数の検索、テキストが検索されている特定の頻度に応じて、メイン ウィンドウに結果を返すことがあります。 モーダル ダイアログ ボックスと同様、モードレス ダイアログ ボックスは、プロパティを使用して結果を返すことができます。 ただし、ダイアログ ボックスを所有しているウィンドウは、それらのプロパティを確認するタイミングを知る必要があります。 これを可能にする方法の 1 つは、ダイアログ ボックスで、テキストが見つかったときに発生するイベントを実装することです。 `FindDialogBox`実装する、`TextFoundEvent`ときに最初この目的のためには、デリゲートが必要です。  
  
 [!code-csharp[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs#textfoundeventhandlercode)]
 [!code-vb[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb#textfoundeventhandlercode)]  
  
 使用して、`TextFoundEventHandler`デリゲート`FindDialogBox`を実装する、`TextFoundEvent`です。  
  
 [!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind2)]  
  
 その結果、`Find`検索結果が見つかった場合は、イベントを発生させることができます。  
  
 [!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind2)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind3)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind3)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind4)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind4)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind5)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind5)]  
  
 そのとき、所有者ウィンドウは、このイベントを登録し、処理する必要があります。  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind2)]  
  
#### <a name="closing-a-modeless-dialog-box"></a>モードレス ダイアログ ボックスを閉じる  
 <xref:System.Windows.Window.DialogResult%2A>システムを使用して、モードレス ダイアログ ボックスを閉じることができます、設定する必要はありません、たとえば、次のメカニズムを提供します。  
  
-   クリックすると、**閉じる**タイトル バーのボタンをクリックします。  
  
-   Alt キーを押しながら F4 キーを押す。  
  
-   選択する**閉じる**から、**システム**メニュー。  
  
 また、コードを呼び出すことができます<xref:System.Windows.Window.Close%2A>ときに、**閉じる**ボタンをクリックします。  
  
 [!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind1)]
 [!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind1)]  
[!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind2)]
[!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind2)]  
  
## <a name="see-also"></a>参照  
 [ポップアップの概要](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [ダイアログ ボックスのサンプル](http://go.microsoft.com/fwlink/?LinkID=159984)  
 [ColorPicker カスタム コントロールのサンプル](http://go.microsoft.com/fwlink/?LinkID=159977)
