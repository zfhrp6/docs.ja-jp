---
title: 'チュートリアル: Win32 での WPF クロックのホスト'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 58e4b1dd311ccd6e1bbab79f4c4dda2207f96eaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>チュートリアル: Win32 での WPF クロックのホスト
配置する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]アプリケーションに、<xref:System.Windows.Interop.HwndSource>を含む HWND を提供する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。 最初に作成、 <xref:System.Windows.Interop.HwndSource>CreateWindow のようなパラメーターを指定します。  指示、<xref:System.Windows.Interop.HwndSource>に関する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内部するコンテンツ。  最後に、HWND のうち、<xref:System.Windows.Interop.HwndSource>です。 このチュートリアルは、混合を作成する方法を示しています。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]オペレーティング システムを reimplements アプリケーション**日付と時刻のプロパティ**ダイアログ。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 参照してください[WPF および Win32 の相互運用](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)です。  
  
## <a name="how-to-use-this-tutorial"></a>このチュートリアルを使用する方法  
 このチュートリアルの相互運用アプリケーションを生成する重要な手順に重点を置いています。 サンプルは、このチュートリアルに基づく[クロックの相互運用の Win32 サンプル](http://go.microsoft.com/fwlink/?LinkID=160051)が、そのサンプルは、最終的な製品の反射です。 既存の開始された場合、このチュートリアル手順について説明[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]独自のプロジェクト、おそらく、既存のプロジェクトを追加して仮定ホストされた[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をアプリケーションにします。 最終的な製品を比較する[クロックの相互運用の Win32 サンプル](http://go.microsoft.com/fwlink/?LinkID=160051)です。  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Windows Presentation Framework Win32 内のチュートリアル (HwndSource)  
 次の図は、このチュートリアルの目的の最終製品を示しています。  
  
 ![日付と時刻のプロパティ ダイアログ ボックス](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")  
  
 C++ を作成することでこのダイアログ ボックスを作成し直すことができます[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]プロジェクト[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、ダイアログ エディターを使用して、次を作成するとします。  
  
 ![日付と時刻のプロパティ ダイアログ ボックス](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")  
  
 (を使用する必要はありません[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]を使用する<xref:System.Windows.Interop.HwndSource>、書き込みに C++ を使用する必要はありませんし[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]をそれを行うには非常に典型的な方法は、プログラムが、このステップワイズのチュートリアルについてにも適しています)。  
  
 配置するために特定の 5 つの手順を実行する必要があります、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ダイアログ ボックスにクロック。  
  
1.  有効にする、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]マネージ コードを呼び出すためのプロジェクト (**/clr**) のプロジェクト設定を変更することによって[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]です。  
  
2.  作成、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>別個の DLL にします。  
  
3.  追加すること[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>内、<xref:System.Windows.Interop.HwndSource>です。  
  
4.  そのため、HWND を取得<xref:System.Windows.Controls.Page>を使用して、<xref:System.Windows.Interop.HwndSource.Handle%2A>プロパティです。  
  
5.  使用して[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]内で、大きい方の HWND を配置する場所を決定する[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]アプリケーション  
  
## <a name="clr"></a>/clr  
 アンマネージこれを有効にするのには、まず[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]マネージ コードをプロジェクトに呼び出すことができます。  /Clr コンパイラ オプションを使用して、使用するため、Main メソッドを調整するために必要な Dll にリンクを使用する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。  
  
 C++ プロジェクト内でマネージ コードの使用を有効にする: win32clock プロジェクトを右クリックし **プロパティ**です。  **全般**プロパティ ページ (既定)、変更を共通言語ランタイム サポート`/clr`です。  
  
 次に、ために必要な Dll への参照を追加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll、PresentationFramework.dll、System.dll、WindowsBase.dll、UIAutomationProvider.dll および UIAutomationTypes.dll です。 (次の手順と c: ドライブにオペレーティング システムをインストールします。)  
  
1.  Win32clock プロジェクトを右クリックし **参照しています.**、そのダイアログ ボックス内。  
  
2.  Win32clock プロジェクトを右クリックし **参照しています.**.  
  
3.  をクリックして**新しい参照の追加**[参照] タブをクリックして、C:\Program \reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll を入力して [ok] をクリックします。  
  
4.  PresentationFramework.dll に対して操作を繰り返します。 C:\Program \reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll です。  
  
5.  WindowsBase.dll に対して操作を繰り返します。 C:\Program \reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll です。  
  
6.  UIAutomationTypes.dll に対して操作を繰り返します。 C:\Program \reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll です。  
  
7.  UIAutomationProvider.dll に対して操作を繰り返します。 C:\Program \reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll です。  
  
8.  をクリックして**新しい参照の追加**System.dll を選択して、をクリックして**OK**です。  
  
9. をクリックして**OK**参照の追加の win32clock プロパティ ページを終了します。  
  
 最後に、追加、`STAThreadAttribute`を`_tWinMain`で使用するためのメソッド[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 この属性は、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]の初期化時[!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]、シングル スレッド アパートメント (STA) はあるモデルに必要なを使用する必要があります[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (および[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)])。  
  
## <a name="create-a-windows-presentation-framework-page"></a>Windows Presentation Framework ページを作成します。  
 次に、定義する DLL を作成、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>です。 作成する最も簡単なは多くの場合、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>スタンドアロン アプリケーションでは、書き込みとデバッグ、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]部分ようにします。  クリックすると、プロジェクトを右クリックして、DLL にそのプロジェクトを変換できますが終わったら、**プロパティ**しようとして、アプリケーション、および Windows クラス ライブラリに出力の種類を変更します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Dll プロジェクト、組み合わせて使用できる、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 、ソリューションを右クリックしてプロジェクト (1 つのソリューションを 2 つのプロジェクトを含む) – **Add\Existing プロジェクト**です。  
  
 使用する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]から dll、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]プロジェクト参照を追加する必要があります。  
  
1.  Win32clock プロジェクトを右クリックし **参照しています.**.  
  
2.  をクリックして**新しい参照の追加**です。  
  
3.  **[プロジェクト]** タブをクリックします。WPFClock を選択し、[ok] をクリックします。  
  
4.  をクリックして**OK**参照の追加の win32clock プロパティ ページを終了します。  
  
## <a name="hwndsource"></a>HwndSource  
 次に、<xref:System.Windows.Interop.HwndSource>させる、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> HWND のようになります。  C++ ファイルには、コードのブロックを追加します。  
  
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
  
 これは、いくつかの説明が使用できるコードの長いです。  最初の部分がさまざまな句すべての呼び出しを完全に修飾する必要はありません。  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 作成する関数を定義し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ、配置、<xref:System.Windows.Interop.HwndSource>周囲、および、HWND を返します。  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 最初に作成、<xref:System.Windows.Interop.HwndSource>パラメーターを持つは CreateWindow に似ています。  
  
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
  
 作成してから、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クラスをコンス トラクターを呼び出してコンテンツします。  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 ページを接続する、 <xref:System.Windows.Interop.HwndSource>:  
  
```  
source->RootVisual = page;  
```  
  
 最後の行で、HWND を返すと、 <xref:System.Windows.Interop.HwndSource>:  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a>Hwnd を配置  
 含む HWND をしたら、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時計の内部には、その HWND を配置する必要があります、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ダイアログ。  そのサイズと場所を渡す場合だけ、HWND を配置する場所がわかっている場合、`GetHwnd`前に定義した関数です。  正確に一致しないことを確認して、Hwnd のいずれかが配置されているので、ダイアログ ボックスの定義にリソース ファイルを使用します。  使用することができます、[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]にダイアログ エディター、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]スタティック コントロールにクロックを移動する (「挿入クロックここで」)、配置に使用して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クロック。  
  
 WM_INITDIALOG を処理する場所を使用する`GetDlgItem`を静的なプレース ホルダーの HWND を取得します。  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 計算するサイズと位置の静的なプレース ホルダーを配置できるように、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]その場所にクロックします。  
  
 RECT 四角形です。  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 非表示にするプレース ホルダーの静的。  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 作成し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時計の HWND をその場所に。  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 実行するチュートリアル興味深いし、実数を生成するために[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時計を作成する必要が、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールをこの時点でクロックします。 分離コード内のいくつかのイベント ハンドラーを持つため、マークアップで行うことができます。 このチュートリアルは、相互運用の概要とコントロールのデザインに関するされませんが後のコードを完了、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クロックが提供されるを構築または各部の意味については不連続指示せず、コード ブロックを図って、ここです。 自由ルック アンド フィールまたはコントロールの機能を変更するには、このコードをお試しください。  
  
 マークアップを次に示します。  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 付随する分離コードを次に示します。  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 最終的な結果は、ようになります。  
  
 ![日付と時刻のプロパティ ダイアログ ボックス](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")  
  
 このスクリーン ショットを作成したコードに、最終結果を比較するを参照してください。[クロックの相互運用の Win32 サンプル](http://go.microsoft.com/fwlink/?LinkID=160051)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Interop.HwndSource>  
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Win32 クロックの相互運用性サンプル](http://go.microsoft.com/fwlink/?LinkID=160051)
