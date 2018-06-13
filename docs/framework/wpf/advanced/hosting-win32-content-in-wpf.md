---
title: WPF での Win32 コンテンツのホスト
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: beb7d5e6e1f934b89bb7516eb7e9bbbaad696238
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547356"
---
# <a name="hosting-win32-content-in-wpf"></a>WPF での Win32 コンテンツのホスト
## <a name="prerequisites"></a>必須コンポーネント  
 参照してください[WPF および Win32 の相互運用](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)です。  
  
## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Windows Presentation Framework (HwndHost) 内の Win32 のチュートリアル  
 再利用する[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]内部コンテンツ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションに、 <xref:System.Windows.Interop.HwndHost>、Hwnd のようになりますコントロールは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。  同様に<xref:System.Windows.Interop.HwndSource>、<xref:System.Windows.Interop.HwndHost>簡単に使用されます: から派生<xref:System.Windows.Interop.HwndHost>および実装`BuildWindowCore`と`DestroyWindowCore`メソッド、インスタンス化し、<xref:System.Windows.Interop.HwndHost>クラスを派生し、その内部に配置、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。  
  
 場合、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ロジックは既に、コントロールとして、パッケージ化されて、`BuildWindowCore`実装がへの呼び出しよりも少し`CreateWindow`です。  たとえば、作成するため、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]の LISTBOX コントロール[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:  
  
```  
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {  
    HWND handle = CreateWindowEx(0, L"LISTBOX",   
    L"this is a Win32 listbox",  
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY  
    | WS_VSCROLL | WS_BORDER,  
    0, 0, // x, y  
    30, 70, // height, width  
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd  
    0, // hmenu  
    0, // hinstance  
    0); // lparam  
  
    return HandleRef(this, IntPtr(handle));  
}  
  
virtual void DestroyWindowCore(HandleRef hwnd) override {  
    // HwndHost will dispose the hwnd for us  
}  
```  
  
 しますが、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]コードはそれほど自己完結型ではありませんか。 そのため、作成できる場合、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]  ダイアログ ボックスし、その内容より大規模なに埋め込む[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。  例は、これには[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]と[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]、これは、異なる言語でまたはコマンドラインで実行することもできます。  
  
 コンパイルは、単純なダイアログを開始、 [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]プロジェクト。  
  
 次に、大きい方に、ダイアログの導入[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。  
  
-   コンパイル、[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]管理対象として (`/clr`)  
  
-   コントロールに、ダイアログ ボックスを有効にします。  
  
-   派生クラスを定義する<xref:System.Windows.Interop.HwndHost>で`BuildWindowCore`と`DestroyWindowCore`メソッド  
  
-   オーバーライド`TranslateAccelerator`ダイアログ キーを処理するメソッド  
  
-   オーバーライド`TabInto`タブ移動をサポートするためにメソッド  
  
-   オーバーライド`OnMnemonic`ニーモニックをサポートするためにメソッド  
  
-   インスタンスを作成、<xref:System.Windows.Interop.HwndHost>サブクラス化し、右下にある配置[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素  
  
### <a name="turn-the-dialog-into-a-control"></a>コントロールに、ダイアログ ボックスを有効にします。  
 子 WS_CHILD と DS_CONTROL スタイルを使用した HWND にダイアログ ボックスを有効にすることができます。  ダイアログ ボックスが定義されているリソース ファイル (.rc) に移動し、ダイアログ ボックスの定義の先頭を探します。  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 2 行目を変更します。  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 このアクションはない完全にパッケージ化自己完結型のコントロールです。呼び出す必要がある`IsDialogMessage()`ように[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]、特定のメッセージを処理できますが、制御の変更は別の HWND 内のそれらのコントロールを作成する場合の簡単な方法を提供します。  
  
## <a name="subclass-hwndhost"></a>サブクラス HwndHost  
 次の名前空間をインポートします。  
  
```  
namespace ManagedCpp  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Input;  
    using namespace System::Windows::Media;  
    using namespace System::Runtime::InteropServices;  
```  
  
 派生クラスを作成し、<xref:System.Windows.Interop.HwndHost>をオーバーライドし、`BuildWindowCore`と`DestroyWindowCore`メソッド。  
  
```  
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {  
    private:  
        HWND dialog;  
  
    protected:   
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {  
            InitializeGlobals();   
            dialog = CreateDialog(hInstance,   
                MAKEINTRESOURCE(IDD_DIALOG1),   
                (HWND) hwndParent.Handle.ToPointer(),  
                (DLGPROC) About);   
            return HandleRef(this, IntPtr(dialog));  
        }  
  
        virtual void DestroyWindowCore(HandleRef hwnd) override {  
            // hwnd will be disposed for us  
        }  
```  
  
 ここで使用して、`CreateDialog`コントロールでは実際にダイアログ ボックスを作成します。  これは内部で呼び出される最初のメソッドの 1 つなので、 [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]、いくつかの標準を行う必要があります[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]後で、定義する関数を呼び出して、初期化と呼ばれる`InitializeGlobals()`:  
  
```  
bool initialized = false;  
    void InitializeGlobals() {  
        if (initialized) return;  
        initialized = true;  
  
        // TODO: Place code here.  
        MSG msg;  
        HACCEL hAccelTable;  
  
        // Initialize global strings  
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);  
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);  
        MyRegisterClass(hInstance);  
```  
  
### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>ダイアログ キーを処理する TranslateAccelerator メソッドをオーバーライドします。  
 このサンプルを実行した場合が表示されたら、ダイアログのコントロールが表示されるが、すべて無視処理は、キーボードの機能 ダイアログ ボックスのダイアログ。  今すぐをオーバーライドする必要があります、`TranslateAccelerator`実装 (からは`IKeyboardInputSink`、インターフェイスを<xref:System.Windows.Interop.HwndHost>を実装)。  このメソッドは、アプリケーションは、WM_KEYDOWN、WM_SYSKEYDOWN が受信すると呼び出されます。  
  
```  
#undef TranslateAccelerator  
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
            ModifierKeys modifiers) override   
        {  
            ::MSG m = ConvertMessage(msg);  
  
            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know   
            // what to do when it reaches the last tab stop  
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {  
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
                TraversalRequest^ request = nullptr;  
  
                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {  
                    // this code should work, but there’s a bug with interop shift-tab in current builds                      
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);  
                }  
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {  
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);  
                }  
  
                if (request != nullptr)  
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);  
  
            }  
  
            // Only call IsDialogMessage for keys it will do something with.  
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {  
                switch (m.wParam) {  
                    case VK_TAB:  
                    case VK_LEFT:  
                    case VK_UP:  
                    case VK_RIGHT:  
                    case VK_DOWN:  
                    case VK_EXECUTE:  
                    case VK_RETURN:  
                    case VK_ESCAPE:  
                    case VK_CANCEL:  
                        IsDialogMessage(dialog, &m);  
                        // IsDialogMessage should be called ProcessDialogMessage --  
                        // it processes messages without ever really telling you  
                        // if it handled a specific message or not  
                        return true;  
                }  
            }  
  
            return false; // not a key we handled  
        }  
```  
  
 これは、いくつかのより詳細な説明が使用することが多くの 2 つのコードです。  最初に、コードを使用して、[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]と[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]マクロ; という名前のマクロは既にことに注意する必要があります`TranslateAccelerator`winuser.h で定義されています。  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 定義するように、`TranslateAccelerator`メソッドおよび not、`TranslateAcceleratorW`メソッドです。  
  
 同様に、アンマネージ winuser.h MSG とマネージの両方がありますが`Microsoft::Win32::MSG`構造体。  使用して、2 つの間で区別できます、 [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::`演算子。  
  
```  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 メッセージの最大数がある、同じデータの両方がこのサンプルでは、明確な変換ルーチンを定義できるように、アンマネージの定義を使用すると便利です。  
  
```  
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {  
    ::MSG m;  
    m.hwnd = (HWND) msg.hwnd.ToPointer();  
    m.lParam = (LPARAM) msg.lParam.ToPointer();  
    m.message = msg.message;  
    m.wParam = (WPARAM) msg.wParam.ToPointer();  
  
    m.time = msg.time;  
  
    POINT pt;  
    pt.x = msg.pt_x;  
    pt.y = msg.pt_y;  
    m.pt = pt;  
  
    return m;  
}  
```  
  
 戻る`TranslateAccelerator`です。  基本的な原則は、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]関数`IsDialogMessage`をできるだけ多くの作業を行うには、`IsDialogMessage`以外のダイアログ ボックスにアクセスできません。 フォーカスを設定する必要があります過去のダイアログ ボックスの最後のコントロールのタブ移動時に、ダイアログの周囲のユーザー タブを実行すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を呼び出して部分`IKeyboardInputSite::OnNoMoreStops`です。  
  
```  
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know   
// what to do when it reaches the last tab stop  
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {  
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
    TraversalRequest^ request = nullptr;  
  
    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {  
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);  
    }  
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {  
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);  
    }  
  
    if (request != nullptr)  
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);  
}  
```  
  
 最後に、`IsDialogMessage` を呼び出します。  役割の 1 つが、`TranslateAccelerator`メソッドは、指示[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]かキーストロークを処理するかどうか。 入力イベントをトンネリングできます処理されなかった場合や、アプリケーションの残りの手順のバブルします。 キーボード メッセージ処理の特性や入力アーキテクチャでは、性質を公開するここでは、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]です。 残念ながら、`IsDialogMessage`返さない任意の方法で特定のキー入力を処理するかどうか。  さらが呼び出されます`DispatchMessage()`キーストローク処理しないでください。  リバース エンジニア リングする必要がように`IsDialogMessage`、知っているキーを処理するためにのみ呼び出します。  
  
```  
// Only call IsDialogMessage for keys it will do something with.  
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {  
    switch (m.wParam) {  
        case VK_TAB:  
        case VK_LEFT:  
        case VK_UP:  
        case VK_RIGHT:  
        case VK_DOWN:  
        case VK_EXECUTE:  
        case VK_RETURN:  
        case VK_ESCAPE:  
        case VK_CANCEL:  
            IsDialogMessage(dialog, &m);  
            // IsDialogMessage should be called ProcessDialogMessage --  
            // it processes messages without ever really telling you  
            // if it handled a specific message or not  
            return true;  
    }  
```  
  
### <a name="override-tabinto-method-to-support-tabbing"></a>この問題のメソッドをオーバーライドしてサポートのタブ移動するには  
 実装している`TranslateAccelerator`、ユーザーがダイアログ ボックス内の周囲タブできますボックスと、大きい値に外 タブ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。  ユーザーがダイアログ ボックスにタブことはできません。  オーバーライドすることを解決する`TabInto`:  
  
```  
public:   
    virtual bool TabInto(TraversalRequest^ request) override {  
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {  
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
            SetFocus(lastTabStop);  
        }  
        else {  
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
            SetFocus(firstTabStop);  
        }  
        return true;  
    }  
```  
  
 `TraversalRequest`パラメーターするがかどうか タブの操作 タブまたは shift キーを押しタブです。  
  
### <a name="override-onmnemonic-method-to-support-mnemonics"></a>ニーモニックをサポートするために OnMnemonic メソッドをオーバーライドします。  
 キーボード処理がほぼ完了しましたが、1 つを使用する必要があるものが見つかりません-ニーモニックが機能しません。  ユーザーは、alt キーを押し F を押すと場合、フォーカス doe いないにジャンプ、"名:"ボックスを編集します。 そのため、オーバーライドする、`OnMnemonic`メソッド。  
  
```  
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {  
    ::MSG m = ConvertMessage(msg);  
  
    // If it's one of our mnemonics, set focus to the appropriate hwnd  
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {  
        int dialogitem = 9999;  
        switch (m.wParam) {  
            case 's': dialogitem = IDOK; break;  
            case 'c': dialogitem = IDCANCEL; break;  
            case 'f': dialogitem = IDC_EDIT1; break;  
            case 'l': dialogitem = IDC_EDIT2; break;  
            case 'p': dialogitem = IDC_EDIT3; break;  
            case 'a': dialogitem = IDC_EDIT4; break;  
            case 'i': dialogitem = IDC_EDIT5; break;  
            case 't': dialogitem = IDC_EDIT6; break;  
            case 'z': dialogitem = IDC_EDIT7; break;  
        }  
        if (dialogitem != 9999) {  
            HWND hwnd = GetDlgItem(dialog, dialogitem);  
            SetFocus(hwnd);  
            return true;  
        }  
    }  
    return false; // key unhandled  
};  
```  
  
 なぜ`IsDialogMessage`ここですか?  これまでに通知できるようにする必要があります。 同じ問題がある[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コードもそうでない、キーストロークが処理されるかどうかをコードおよび`IsDialogMessage`を行うことはできません。  2 つ目の問題がある、ため`IsDialogMessage`対象を絞った HWND がダイアログ ボックスの内側にない場合、ニーモニックの処理を拒否します。  
  
### <a name="instantiate-the-hwndhost-derived-class"></a>インスタンスを作成、HwndHost 派生クラス  
 最後に、すべてのキーとタブのサポートは、配置では、これで配置できる、 <xref:System.Windows.Interop.HwndHost> 、大きい方に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。  メイン アプリケーションが記述されている場合[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、適切な場所に配置する最も簡単な方法は、空のままにする<xref:System.Windows.Controls.Border>要素を配置する場所、<xref:System.Windows.Interop.HwndHost>です。  ここで、作成、<xref:System.Windows.Controls.Border>という`insertHwndHostHere`:  
  
```  
<Window x:Class="WPFApplication1.Window1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    Title="Windows Presentation Framework Application"  
    Loaded="Window1_Loaded"  
    >  
    <StackPanel>  
        <Button Content="WPF button"/>  
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>  
        <Button Content="WPF button"/>  
    </StackPanel>  
</Window>  
```  
  
 インスタンスを作成するコード シーケンスで適切な場所を探しますにしてから、<xref:System.Windows.Interop.HwndHost>に接続するには<xref:System.Windows.Controls.Border>します。  この例では内に配置することのコンス トラクター、<xref:System.Windows.Window>クラスを派生します。  
  
```  
public partial class Window1 : Window {  
    public Window1() {  
    }  
  
    void Window1_Loaded(object sender, RoutedEventArgs e) {  
        HwndHost host = new ManagedCpp.MyHwndHost();  
        insertHwndHostHere.Child = host;  
    }  
}  
```  
  
 提供します。  
  
 ![WPF アプリケーションのスクリーン ショット](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")  
  
## <a name="see-also"></a>関連項目  
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
