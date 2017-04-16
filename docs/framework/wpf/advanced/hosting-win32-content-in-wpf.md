---
title: "WPF での Win32 コンテンツのホスト | Microsoft Docs"
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
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# WPF での Win32 コンテンツのホスト
## 必須コンポーネント  
 「[WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)」を参照してください。  
  
## Windows Presentation Framework \(HwndHost\) 内の Win32 のチュートリアル  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーション内で [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コンテンツを再利用するには、<xref:System.Windows.Interop.HwndHost> を使用します。<xref:System.Windows.Interop.HwndHost> は、HWND を [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのように見せるコントロールです。  <xref:System.Windows.Interop.HwndSource> と同様に、<xref:System.Windows.Interop.HwndHost> は簡単に使用できます。<xref:System.Windows.Interop.HwndHost> から派生し、`BuildWindowCore` メソッドと `DestroyWindowCore` メソッドを実装して、<xref:System.Windows.Interop.HwndHost> 派生クラスをインスタンス化し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーション内に配置します。  
  
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ロジックが既にコントロールとしてパッケージ化されている場合、`BuildWindowCore` 実装は、`CreateWindow` の呼び出しとほとんど変わりません。  たとえば、[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] で [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX コントロールを作成するには、次のようにします。  
  
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
  
 しかし、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コードがあまり自己完結的ではないこともあります。  その場合は、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ダイアログ ボックスを作成して、そのコンテンツをより大きい [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションに埋め込みます。  サンプルでは、これを [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] と [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] で示していますが、別の言語またはコマンド ラインで実行することも可能です。  
  
 まず、[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] プロジェクトにコンパイルされる単純なダイアログから始めます。  
  
 次に、より大きい [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションにダイアログを導入します。  
  
-   [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] をマネージとしてコンパイルします \(`/clr`\)。  
  
-   ダイアログをコントロールに変換します。  
  
-   <xref:System.Windows.Interop.HwndHost> の派生クラスを `BuildWindowCore` メソッドと `DestroyWindowCore` メソッドで定義します。  
  
-   `TranslateAccelerator` メソッドをオーバーライドして、ダイアログ キーを処理します。  
  
-   `TabInto` メソッドをオーバーライドして、Tab キーによる移動をサポートします。  
  
-   `OnMnemonic` メソッドをオーバーライドして、ニーモニックをサポートします。  
  
-   <xref:System.Windows.Interop.HwndHost> サブクラスをインスタンス化し、それを適切な [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素の下に置きます。  
  
### ダイアログをコントロールに変換します。  
 WS\_CHILD スタイルと DS\_CONTROL スタイルを使用して、ダイアログ ボックスを子 HWND に変換できます。  ダイアログが定義されているリソース ファイル \(.rc\) に移動し、次のようなダイアログ定義の先頭を見つけます。  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 2 行目を次のように変更します。  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 この操作では、ダイアログが自己完結的なコントロールに完全にパッケージ化されることはありません。[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] が特定のメッセージを処理できるように、`IsDialogMessage()` を呼び出す必要があります。ただし、コントロールを変更すると、それらのコントロールを別の HWND に簡単に置くことができます。  
  
## サブクラス HwndHost  
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
  
 次に、<xref:System.Windows.Interop.HwndHost> の派生クラスを作成し、`BuildWindowCore` メソッドと `DestroyWindowCore` メソッドをオーバーライドします。  
  
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
  
 ここでは、`CreateDialog` を使用して実際のコントロールであるダイアログ ボックスを作成します。  これは、[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] 内で最初に呼び出されるメソッドの 1 つであるため、後から定義する、`InitializeGlobals()` という名前の関数を呼び出して標準の [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 初期化を実行することも必要です。  
  
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
  
### TranslateAccelerator Method のオーバーライドによるダイアログ キーの処理  
 このサンプルをこのまま実行すると、ダイアログ コントロールは表示されますが、ダイアログ ボックスが実際に使用できるようになるためのキーボード処理は、すべて無視されます。  ここでは、\(<xref:System.Windows.Interop.HwndHost> が実装するインターフェイスである `IKeyboardInputSink` から取得する\) `TranslateAccelerator` 実装をオーバーライドする必要があります。  このメソッドは、アプリケーションが WM\_KEYDOWN および WM\_SYSKEYDOWN を受け取ったときに呼び出されます。  
  
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
  
 この例には多くのコードが含まれているため、そのいくつかについて詳しく説明します。  最初に、[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] および [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] のマクロを使用するコードについて、`TranslateAccelerator` という名前のマクロが既に存在し、winuser.h で次のように定義されていることに注意する必要があります。  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 このため、`TranslateAcceleratorW` メソッドではなく `TranslateAccelerator` メソッドを定義する必要があります。  
  
 同様に、アンマネージ winuser.h MSG とマネージ `Microsoft::Win32::MSG` struct の両方が存在します。  [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` 演算子を使用して、この 2 つの MSG のあいまいさを解消できます。  
  
```  
  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 2 つの MSG のデータは同じですが、アンマネージ定義を使用した方が簡単な場合があるため、このサンプルでは次のように明確な変換ルーチンを定義できます。  
  
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
  
 `TranslateAccelerator` に戻ります。  基本的な原則は、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 関数 `IsDialogMessage` を呼び出して、できる限り多くの作業を実行することですが、`IsDialogMessage` はダイアログ外のものには一切アクセスできません。ユーザーがダイアログ内を Tab キーで移動し、Tab キーがダイアログ内の最後のコントロールを超える場合は、`IKeyboardInputSite::OnNoMoreStops` を呼び出してフォーカスを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の部分に設定する必要があります。  
  
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
  
 最後に、`IsDialogMessage` を呼び出します。  ただし、`TranslateAccelerator` メソッドが行う処理の 1 つは、キーストロークを処理しているかどうかを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に伝えることです。  キーストロークを処理していない場合、入力イベントはアプリケーションの残りをトンネリングおよびバブリングできます。  ここで、キーボード メッセージ処理の特性と、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] の入力アーキテクチャの性質を公開します。  `IsDialogMessage` は、特定のキーストロークを処理しているかどうかの値を返しません。  さらに、処理する必要のないキーストロークで `DispatchMessage()` を呼び出します。  このため、`IsDialogMessage` をリバースエンジニアリングして、処理することがわかっているキーに対してのみ `IsDialogMessage` を呼び出す必要があります。  
  
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
  
### TabInto メソッドのオーバーライドによる Tab キーによる移動のサポート  
 `TranslateAccelerator` の実装が完了したので、ユーザーはダイアログ ボックス内を Tab キーで移動し、ダイアログ ボックスからより大きい [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションへ移動することができます。  ただし、ユーザーはダイアログ ボックスに Tab キーで戻ることができません。  この問題を解決するためには、`TabInto` をオーバーライドします。  
  
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
  
 `TraversalRequest` パラメーターは、Tab キーのアクションが Tab キーであるか Shift \+ Tab キーであるかを示します。  
  
### OnMnemonic メソッドのオーバーライドによるニーモニックのサポート  
 キーボード処理はほぼ完了ですが、1 つ残っている処理があります。それはニーモニックが機能しないという点です。  ユーザーが Alt キーを押しながら F キーを押しても、\[First name:\] ボックスにはジャンプしません。  このため、`OnMnemonic` メソッドを次のようにオーバーライドします。  
  
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
  
 ここでは、なぜ `IsDialogMessage` を呼び出さないのでしょうか。  前述したとおり、コードがキーストロークを処理したかどうかを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に伝える必要があるにもかかわらず、`IsDialogMessage` はそれを実行できません。  また、フォーカスがある HWND がダイアログ ボックス内にない場合、ニーモニックの処理を `IsDialogMessage` が拒否するという問題もあります。  
  
### HwndHost 派生クラスのインスタンス化  
 最後に、すべてのキーと Tab キーがサポートされるようになったので、<xref:System.Windows.Interop.HwndHost> をより大きい [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションに入れることができます。  メインのアプリケーションが [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で記述される場合、<xref:System.Windows.Interop.HwndHost> を正しい場所に入れる最も簡単な方法は、<xref:System.Windows.Interop.HwndHost> を入れる空の <xref:System.Windows.Controls.Border> 要素を残しておくことです。  ここで、`insertHwndHostHere` という名前の <xref:System.Windows.Controls.Border> を作成します。  
  
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
  
 後は、コード シーケンス内で <xref:System.Windows.Interop.HwndHost> をインスタンス化するのに適した場所を見つけ、それを <xref:System.Windows.Controls.Border> に接続するだけです。  この例では、<xref:System.Windows.Window> 派生クラスのコンストラクター内に入れます。  
  
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
  
 次のような画面が表示されます。  
  
 ![WPF アプリケーションのスクリーンショット](../../../../docs/framework/wpf/advanced/media/interoparch09.png "InteropArch09")  
  
## 参照  
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)