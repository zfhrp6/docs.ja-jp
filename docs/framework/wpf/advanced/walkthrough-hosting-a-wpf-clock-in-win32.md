---
title: "チュートリアル: Win32 での WPF クロックのホスト | Microsoft Docs"
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
  - "相互運用性 [WPF], チュートリアル"
  - "相互運用性 [WPF], Win32"
  - "Win32 コード, WPF 相互運用"
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# チュートリアル: Win32 での WPF クロックのホスト
[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーション内に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を配置するには、<xref:System.Windows.Interop.HwndSource> を使用します。<xref:System.Windows.Interop.HwndSource> は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを格納する HWND を提供します。  まず、<xref:System.Windows.Interop.HwndSource> を作成し、CreateWindow に似たパラメーターを渡します。  次に、<xref:System.Windows.Interop.HwndSource> 内に格納する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツについて <xref:System.Windows.Interop.HwndSource> に通知します。  最後に、<xref:System.Windows.Interop.HwndSource> から HWND を取得します。  このチュートリアルでは、オペレーティング システムの **\[日付と時刻のプロパティ\]** ダイアログを再実装する混在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーション内に作成する方法について説明します。  
  
## 必須コンポーネント  
 「[WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)」を参照してください。  
  
## このチュートリアルの使用方法  
 このチュートリアルでは、相互運用アプリケーションを作成するための重要な手順に重点を置いて説明します。  このチュートリアルは、[Win32 クロック相互運用のサンプル](http://go.microsoft.com/fwlink/?LinkID=160051)によって補足されます。ただし、このサンプルは最終結果を反映しています。  このチュートリアルでは、開発者が独自の既存の [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プロジェクト \(おそらく以前から存在するプロジェクト\) から開始し、ホストされる [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] をアプリケーションに追加すると仮定して手順を説明します。  最終結果は [Win32 クロック相互運用のサンプル](http://go.microsoft.com/fwlink/?LinkID=160051)と比較できます。  
  
## Win32 \(HwndSource\) 内の Windows Presentation Framework のチュートリアル  
 このチュートリアルの対象となるダイアログを次の図に示します。  
  
 ![&#91;日付と時刻のプロパティ&#93; ダイアログ ボックス](../../../../docs/framework/wpf/advanced/media/interoparch06.png "InteropArch06")  
  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] で C\+\+ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プロジェクトを作成し、ダイアログ エディターを使用して次のダイアログを作成することにより、このダイアログを再作成することができます。  
  
 ![&#91;日付と時刻のプロパティ&#93; ダイアログ ボックス](../../../../docs/framework/wpf/advanced/media/interoparch07.png "InteropArch07")  
  
 \(<xref:System.Windows.Interop.HwndSource> を使用するのに [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] を使用する必要はなく、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プログラムを作成するのに C\+\+ を使用する必要もありません。ただし、これらを使用するのが一般的なやり方であり、チュートリアルの段階的な説明に役立ちます。\)  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クロックをダイアログ内に配置するには、次の 5 つのサブステップを実行する必要があります。  
  
1.  [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] でプロジェクト設定を変更して、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プロジェクトがマネージ コード \(**\/clr**\) を呼び出すことができるようにします。  
  
2.  別の DLL 内に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> を作成します。  
  
3.  その [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> を <xref:System.Windows.Interop.HwndSource> 内に配置します。  
  
4.  <xref:System.Windows.Interop.HwndSource.Handle%2A> プロパティを使用して、この <xref:System.Windows.Controls.Page> の HWND を取得します。  
  
5.  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] を使用して、より大きな[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーション内の HWND の配置場所を決定します。  
  
## \/clr  
 最初の手順は、このアンマネージ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プロジェクトを、マネージ コードを呼び出すことができるプロジェクトに変更することです。  \/clr コンパイラ オプションを使用して必要な DLL にリンクし、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で使用する Main メソッドを変更します。  
  
 C\+\+ プロジェクト内でマネージ コードを使用できるようにするには、win32clock プロジェクトを右クリックして \[プロパティ\] をクリックします。  \[全般\] プロパティ ページ \(既定\) で、共通言語ランタイム サポートを `/clr` に変更します。  
  
 次に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で必要な DLL \(PresentationCore.dll、PresentationFramework.dll、System.dll、WindowsBase.dll、UIAutomationProvider.dll、および UIAutomationTypes.dll\) への参照を追加します   \(次の手順では、オペレーティング システムが C: ドライブにインストールされていると仮定します\)。  
  
1.  win32clock プロジェクトを右クリックして **\[参照設定\]** をクリックし、表示されるダイアログで次の手順を実行します。  
  
2.  win32clock プロジェクトを右クリックして **\[参照設定\]** をクリックします。  
  
3.  \[新しい参照の追加\] をクリックして \[参照\] タブをクリックし、「C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\PresentationCore.dll」と入力して \[OK\] をクリックします。  
  
4.  PresentationFramework.dll \(C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\PresentationFramework.dll\) について同様の手順を繰り返します。  
  
5.  WindowsBase.dll \(C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\WindowsBase.dll\) について同様の手順を繰り返します。  
  
6.  UIAutomationTypes.dll \(C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\UIAutomationTypes.dll\) について同様の手順を繰り返します。  
  
7.  UIAutomationProvider.dll \(C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\UIAutomationProvider.dll\) について同様の手順を繰り返します。  
  
8.  **\[新しい参照の追加\]** をクリックし、System.dll を選択して **\[OK\]** をクリックします。  
  
9. \[OK\] をクリックして、参照を追加するための win32clock プロパティ ページを閉じます。  
  
 最後に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で使用する `_tWinMain` メソッドに `STAThreadAttribute` を追加します。  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 この属性は、[!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)] を初期化するタイミングと、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] \(および [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]\) で必要なシングル スレッド アパートメント モデル \(STA\) を使用する必要があることを[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] に通知します。  
  
## Windows Presentation Framework ページの作成  
 次に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> を定義する DLL を作成します。  通常は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> をスタンドアロン アプリケーションとして作成し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 部分を単独で記述およびデバッグするのが最も簡単です。  作成が完了したら、そのプロジェクトを DLL に変更することができます。DLL に変更するには、プロジェクトを右クリックして \[プロパティ\] をクリックし、アプリケーションに移動して出力の種類を Windows クラス ライブラリに変更します。  
  
 その後、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll プロジェクトと [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プロジェクトを結合できます \(2 つのプロジェクトを含むソリューション\)。これを行うには、ソリューションを右クリックして **\[既存プロジェクトの追加\]** をクリックします。  
  
 この [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll を [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プロジェクトから使用するには、次の手順を実行して参照を追加する必要があります。  
  
1.  win32clock プロジェクトを右クリックして **\[参照設定\]** をクリックします。  
  
2.  **\[新しい参照の追加\]** をクリックします。  
  
3.  **\[プロジェクト\]** タブをクリックします。  WPFClock を選択して \[OK\] をクリックします。  
  
4.  \[OK\] をクリックして、参照を追加するための win32clock プロパティ ページを閉じます。  
  
## HwndSource  
 次に、<xref:System.Windows.Interop.HwndSource> を使用して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> を HWND に似た外観にします。  次のコード ブロックを C\+\+ ファイルに追加します。  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
  
    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
        HwndSource^ source = gcnew HwndSource(  
            0, // class style  
            WS_VISIBLE | WS_CHILD, // style  
            0, // exstyle  
            x, y, width, height,  
            "hi", // NAME  
            IntPtr(parent)        // parent window   
            );  
  
        UIElement^ page = gcnew WPFClock::Clock();  
        source->RootVisual = page;  
        return (HWND) source->Handle.ToPointer();  
    }  
}  
}  
```  
  
 これは長いコードであり、若干の説明を加えることができます。  先頭にはさまざまな句が記述されています。これにより、すべての呼び出しを完全に修飾する必要がなくなります。  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 次に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを作成し、その周りに <xref:System.Windows.Interop.HwndSource> を配置して HWND を返す関数を定義します。  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 最初に、CreateWindow と同様のパラメーターを指定して <xref:System.Windows.Interop.HwndSource> を作成します。  
  
```  
HwndSource^ source = gcnew HwndSource(  
    0, // class style  
    WS_VISIBLE | WS_CHILD, // style  
    0, // exstyle  
    x, y, width, height,  
    "hi", // NAME  
    IntPtr(parent) // parent window   
    );  
```  
  
 次に、コンストラクターを呼び出して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ クラスを作成します。  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 次に、ページを <xref:System.Windows.Interop.HwndSource> に関連付けます。  
  
```  
source->RootVisual = page;  
```  
  
 最後の行で <xref:System.Windows.Interop.HwndSource> の HWND を返します。  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## Hwnd の配置  
 以上で [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クロックを含む HWND の作成が完了しました。次に、この HWND を [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ダイアログ内に配置する必要があります。  HWND の配置場所がわかっている場合は、先ほど定義した `GetHwnd` 関数に HWND のサイズと位置を渡すだけで済みます。  ただし、ここではリソース ファイルを使用してダイアログを定義したため、HWND の正確な配置場所がわかりません。  [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] のダイアログ エディターを使用すると、クロックの配置場所 \("ここにクロックを挿入"\) に [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] スタティック コントロールを配置し、それを使用して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クロックを配置することができます。  
  
 WM\_INITDIALOG を処理する場合は、`GetDlgItem` を使用して STATIC プレースホルダーの HWND を取得します。  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 次に、STATIC プレースホルダーのサイズと位置を計算し、その場所に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クロックを配置できるようにします。  
  
 RECT 四角形  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 次に、STATIC プレースホルダーを非表示にします。  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 その場所に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クロック HWND を作成します。  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 このチュートリアルを有意義なものにし、実際の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クロックを作成するには、この時点で [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クロック コントロールを作成する必要があります。  通常、このコントロールは、分離コード内のいくつかのイベント ハンドラーと共に、マークアップで作成します。  このチュートリアルは、相互運用に関するものであり、コントロール設計に関するものではありません。したがって、ここでは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クロックのコード全体をコード ブロックとして提供し、個々の作成手順や各部分の意味については説明しません。  このコードを修正し、コントロールの外観や機能を変更してみることをお勧めします。  
  
 マークアップを次に示します。  
  
 [!code-xml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 関連する分離コードを次に示します。  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 最終結果は次のようになります。  
  
 ![&#91;日付と時刻のプロパティ&#93; ダイアログ ボックス](../../../../docs/framework/wpf/advanced/media/interoparch08.png "InteropArch08")  
  
 最終結果とこのスクリーンショットを生成したコードを比較する場合は、[Win32 クロック相互運用のサンプル](http://go.microsoft.com/fwlink/?LinkID=160051)を参照してください。  
  
## 参照  
 <xref:System.Windows.Interop.HwndSource>   
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [Win32 クロック相互運用のサンプル](http://go.microsoft.com/fwlink/?LinkID=159995)