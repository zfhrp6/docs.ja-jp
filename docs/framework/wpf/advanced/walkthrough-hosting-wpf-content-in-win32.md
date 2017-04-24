---
title: "チュートリアル: Win32 での WPF コンテンツのホスト | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ホスト (WPF コンテンツを Win32 ウィンドウで)"
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# チュートリアル: Win32 での WPF コンテンツのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。  ただし、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] コードにかなりの投資がある場合は、元のコードを書き換えるより、アプリケーションに [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の機能を追加するほうがより効果的であることがあります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをホストする簡単なメカニズムがあります。  
  
 このチュートリアルでは、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをホストするサンプル アプリケーション \(「[Win32 ウィンドウのサンプルで WPF コンテンツをホストする](http://go.microsoft.com/fwlink/?LinkID=160004)」\) の記述方法について説明します。  このサンプルを拡張すると、いずれの [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウでもホストできます。  マネージ コードとアンマネージ コードの混在が関係しているため、このアプリケーションは [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] で記述されます。  
  
   
  
<a name="requirements"></a>   
## 必要条件  
 このチュートリアルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プログラミングの基礎知識があることを前提としています。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のプログラミングの基本的な概要については、「[作業の開始](../../../../docs/framework/wpf/getting-started/index.md)」を参照してください。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] のプログラミングの概要については、この主題に関する数多くの書籍、特に「*Programming Windows*」 \(Charles Petzold 著\) を参照することをお勧めします。  
  
 このチュートリアルに付属するサンプルは [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] で実装されているため、このチュートリアルでは [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] を使用した [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] のプログラミングの知識があることと、マネージ コード プログラミングを理解していることを前提としています。  [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] の知識があることは、役立ちますが、必須ではありません。  
  
> [!NOTE]
>  このチュートリアルには、関連するサンプルからのコード例が多数含まれています。  しかし、読みやすくするため、完全なサンプル コードは含まれていません。  完全なサンプル コードについては、「[Win32 ウィンドウのサンプルで WPF コンテンツをホストする](http://go.microsoft.com/fwlink/?LinkID=160004)」を参照してください。  
  
<a name="basic_procedure"></a>   
## 基本手順  
 このセクションでは、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをホストするために使用する基本手順について概説します。  残りのセクションでは、各手順の詳細について説明します。  
  
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] をホストする鍵となるのが、<xref:System.Windows.Interop.HwndSource> クラスです。  このクラスは [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをラップし、子ウィンドウとして [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] に組み込めるようにすることができます。  次の方法では、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] および [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を単一のアプリケーションに統合します。  
  
1.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをマネージ クラスとして実装します。  
  
2.  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションを [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] で実装します。  既存のアプリケーションとアンマネージの [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] コードで使用を開始する場合、通常は、プロジェクトの設定を `/clr` コンパイラ フラグを含めるように変更して、マネージ コードを呼び出せるようにします。  
  
3.  スレッド処理モデルをシングル スレッド アパートメント \(STA: Single Threaded Apartment\) に設定します。  
  
4.  ウィンドウのプロシージャで [WM\_CREATE](http://msdn.microsoft.com/library/ms632619.aspx) を処理してから、以下を実行します。  
  
    1.  新しい <xref:System.Windows.Interop.HwndSource> オブジェクトを、親ウィンドウがその `parent` パラメーターとなるように指定して作成します。  
  
    2.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ クラスのインスタンスを作成します。  
  
    3.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ オブジェクトへの参照を <xref:System.Windows.Interop.HwndSource> の <xref:System.Windows.Interop.HwndSource.RootVisual%2A> プロパティに割り当てます。  
  
    4.  コンテンツの HWND を取得します。  <xref:System.Windows.Interop.HwndSource> オブジェクトの <xref:System.Windows.Interop.HwndSource.Handle%2A> プロパティにウィンドウ ハンドル \(HWND\) が格納されます。  アプリケーションのアンマネージ部分で使用できる HWND を取得するには、`Handle.ToPointer()` を HWND にキャストします。  
  
5.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照を保持する静的フィールドを含むマネージ クラスを実装します。  このクラスを使用すると、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コードから [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照を取得できるようになります。  
  
6.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを静的フィールドに割り当てます。  
  
7.  ハンドラーを 1 つ以上の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベントにアタッチして、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツから通知を受信します。  
  
8.  静的フィールドに格納した参照を使用して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツと通信し、プロパティの設定などを行います。  
  
> [!NOTE]
>  また、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを実装することもできます。  ただし、このコンテンツは [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] として別にコンパイルしてから、その [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] に [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションから参照する必要があります。  手順の残りの部分は、前述の手順と同様です。  
  
<a name="implementing_the_application"></a>   
## ホスト アプリケーションの実装  
 このセクションでは、基本的な [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをホストする方法について説明します。  コンテンツ自体は、マネージ クラスとして [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] に実装されます。  ほとんどの部分が、簡単な [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のプログラミングです。  コンテンツの実装の重要な側面については、「[WPF コンテンツの実装](#implementing_the_wpf_page)」で説明します。  
  
<a name="autoNestedSectionsOUTLINE1"></a>   
-   [基本的なアプリケーション](#the_basic_application)  
  
-   [WPF コンテンツのホスティング](#hosting_the_wpf_page)  
  
-   [WPF コンテンツへの参照の保持](#holding_a_reference)  
  
-   [WPF コンテンツとの通信](#communicating_with_the_page)  
  
<a name="the_basic_application"></a>   
### 基本的なアプリケーション  
 ホスト アプリケーションの開始点は、[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] テンプレートを作成することでした。  
  
1.  [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] を開き、**\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックします。  
  
2.  [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] プロジェクトの種類の一覧から、**Win32** を選択します。  既定の言語が [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] でない場合は、このプロジェクトの種類は **\[他の言語\]** の下にあります。  
  
3.  **\[Win32 プロジェクト\]** テンプレートをクリックし、プロジェクトに名前を割り当ててから、**\[OK\]** をクリックして、**\[Win32 アプリケーション\] ウィザード**を開始します。  
  
4.  ウィザードの既定の設定をそのまま承認し、**\[完了\]** をクリックしてプロジェクトを開始します。  
  
 このテンプレートは、次のような基本的な [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションを作成します。  
  
-   アプリケーションのエントリ ポイント。  
  
-   関連するウィンドウ プロシージャ \(WndProc\) を含むウィンドウ。  
  
-   **\[ファイル\]** と **\[ヘルプ\]** の各見出しを含むメニュー。  **\[ファイル\]** メニューには、アプリケーションを閉じる **\[終了\]** 項目があります。  **\[ヘルプ\]** メニューには、簡単なダイアログ ボックスを起動する **\[バージョン情報\]** 項目があります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをホストするためにコードを記述する前に、基本のテンプレートに対して 2 つの変更を加える必要があります。  
  
 1 つ目は、プロジェクトをマネージ コードとしてコンパイルすることです。  既定では、プロジェクトはアンマネージ コードとしてコンパイルされます。  ただし、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] はマネージ コードで実装されているため、プロジェクトは状況に応じてコンパイルする必要があります。  
  
1.  **ソリューション エクスプローラー**で、プロジェクト名を右クリックし、コンテキスト メニューの **\[プロパティ\]** をクリックして、**\[プロパティ ページ\]** ダイアログ ボックスを開始します。  
  
2.  左ペインにあるツリー ビューで、**\[構成プロパティ\]** を選択します。  
  
3.  右ペインの **\[プロジェクトの詳細\]** の一覧から、”**共通言語ランタイム** サポート” を選択します。  
  
4.  ドロップダウン リスト ボックスから**共通言語ランタイム サポート \(\/clr\)** を選択します。  
  
> [!NOTE]
>  このコンパイラ フラグを使用すると、アプリケーションでマネージ コードを使用できますが、アンマネージ コードは以前と同様にコンパイルされます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、シングル スレッド アパートメント \(STA\) スレッド処理モデルを使用します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのコードで正常に機能するためには、エントリ ポイントに属性を適用してアプリケーションのスレッド処理モデルを STA に設定する必要があります。  
  
 [!code-cpp[Win32HostingWPFPage#WinMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]  
  
<a name="hosting_the_wpf_page"></a>   
### WPF コンテンツのホスティング  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは、単純なアドレス入力アプリケーションです。  それは、ユーザー名やアドレスなどを取得する複数の <xref:System.Windows.Controls.TextBox> コントロールで構成されています。  さらに、**\[OK\]** と **\[キャンセル\]** という 2 つの <xref:System.Windows.Controls.Button> コントロールがあります。  ユーザーが **\[OK\]** をクリックすると、ボタンの <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラーは <xref:System.Windows.Controls.TextBox> コントロールからデータを収集し、それを対応するプロパティに割り当て、カスタム イベント `OnButtonClicked` を発生させます。  ユーザーが **\[キャンセル\]** をクリックすると、ハンドラーは単に `OnButtonClicked` を発生させます。  `OnButtonClicked` のイベント引数オブジェクトには、どのボタンをクリックしたかを示すブール型フィールドが含まれています。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをホストするコードは、ホスト ウィンドウで [WM\_CREATE](http://msdn.microsoft.com/library/ms632619.aspx) 通知を行うためにハンドラーに実装されます。  
  
 [!code-cpp[Win32HostingWPFPage#WMCreate](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]  
  
 `GetHwnd` メソッドは、サイズと位置の情報および親ウィンドウ ハンドルを取得し、ホストされた [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのウィンドウ ハンドルを返します。  
  
> [!NOTE]
>  `System::Windows::Interop` 名前空間に `#using` ディレクティブを使用することはできません。  使用すると、その名前空間の <xref:System.Windows.Interop.MSG> 構造体と winuser.h で宣言した MSG 構造体の間で名前の競合が発生します。  代わりに、その名前空間のコンテンツにアクセスするための完全修飾名を使用する必要があります。  
  
 [!code-cpp[Win32HostingWPFPage#GetHwnd](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のコンテンツを直接アプリケーション ウィンドウでホストすることはできません。  代わりに、まず [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをラップするための <xref:System.Windows.Interop.HwndSource> オブジェクトを作成します。  このオブジェクトは、基本的に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをホストするように設計されたウィンドウです。  <xref:System.Windows.Interop.HwndSource> オブジェクトをアプリケーションの一部である [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウの子として作成することで、このオブジェクトを親ウィンドウでホストします。  <xref:System.Windows.Interop.HwndSource> コンストラクターのパラメーターには、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] の子ウィンドウの作成時に CreateWindow に渡される情報とほとんど同じ情報が含まれています。  
  
 次に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ オブジェクトのインスタンスを作成します。  この場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは、[!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] を使用して、別のクラス `WPFPage` として実装されます。  さらに、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で実装することもできます。  ただし、これを行うためには、別のプロジェクトをセットアップしてから、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] としてビルドする必要があります。  プロジェクトにその [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] への参照を追加し、その参照を使用して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのインスタンスを作成します。  
  
 <xref:System.Windows.Interop.HwndSource> の <xref:System.Windows.Interop.HwndSource.RootVisual%2A> プロパティに [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照を割り当てることで、子ウィンドウに [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを表示します。  
  
 次のコード行は、イベント ハンドラー `WPFButtonClicked` を [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツの `OnButtonClicked` イベントにアタッチしています。  このハンドラーは、ユーザーが **\[OK\]** または **\[キャンセル\]** ボタンをクリックすると呼び出されます。  このイベント ハンドラーの詳細な説明については「[communicating\_with\_the\_WPF コンテンツ](#communicating_with_the_page)」を参照してください。  
  
 示されているコードの最後の行は、<xref:System.Windows.Interop.HwndSource> オブジェクトに関連付けられているウィンドウ ハンドル \(HWND\) を返します。  このハンドルは、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コードから使用してホストされたウィンドウにメッセージを送信することができます。ただし、サンプルではこれはできません。  <xref:System.Windows.Interop.HwndSource> オブジェクトは、メッセージを受信するたびにイベントを発生させます。  メッセージを処理するには、<xref:System.Windows.Interop.HwndSource.AddHook%2A> メソッドを呼び出してメッセージ ハンドラーをアタッチしてから、そのハンドラーでメッセージを処理します。  
  
<a name="holding_a_reference"></a>   
### WPF コンテンツへの参照の保持  
 多くのアプリケーションでは、後で [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツと通信することができます。  たとえば、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのプロパティを変更したり、場合によっては <xref:System.Windows.Interop.HwndSource> オブジェクトが異なる [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをホストするようにしたりできます。  そのためには、<xref:System.Windows.Interop.HwndSource> オブジェクトまたは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照が必要です。  <xref:System.Windows.Interop.HwndSource> オブジェクトと関連する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは、ウィンドウ ハンドルを破棄するまでメモリに残ります。  ただし、<xref:System.Windows.Interop.HwndSource> オブジェクトに割り当てる変数は、ウィンドウ プロシージャから戻ると同時にスコープの外に出ます。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションでこの問題を処理するためによく使用される方法は、静的変数またはグローバル変数を使用することです。  残念ながら、このような変数の種類に対してマネージ オブジェクトを割り当てることはできません。  <xref:System.Windows.Interop.HwndSource> オブジェクトに関連付けられているウィンドウ ハンドルを、グローバル変数または静的変数に割り当てることができますが、オブジェクト自体にアクセスすることはできません。  
  
 この問題の最も簡単な解決法は、静的フィールドのセットを含むマネージ クラスを実装して、アクセスが必要なすべてのマネージ オブジェクトへの参照を保持することです。  サンプルでは、`WPFPageHost` クラスを使用して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照、および後でユーザーが変更する可能性があるプロパティの数の初期値を保持します。  これは、ヘッダーで定義します。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageHost](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]  
  
 `GetHwnd` 関数の後半部分では、後に、`myPage` がスコープ内にある間に使用するため、対象のフィールドに値を割り当てます。  
  
<a name="communicating_with_the_page"></a>   
### WPF コンテンツとの通信  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツとの通信には次の 2 種類があります。  アプリケーションは、ユーザーが **\[OK\]** または **\[キャンセル\]** ボタンをクリックすると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツから情報を受信します。  アプリケーションには、背景色や既定のフォント サイズなどのさまざまな [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのプロパティをユーザーが変更できるようにする [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] があります。  
  
 前述のように、ユーザーがいずれかのボタンをクリックすると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは `OnButtonClicked` イベントを発生させます。  アプリケーションは、これらの通知を受信するため、このイベントにハンドラーをアタッチします。  **\[OK\]** ボタンがクリックされた場合、ハンドラーはユーザー情報を [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツから取得し、一連の静的コントロールで表示します。  
  
 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]  
  
 ハンドラーは、カスタム イベント引数オブジェクトを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のコンテンツ、`MyPageEventArgs` から受信します。  **\[OK\]** ボタンをクリックした場合、オブジェクトの `IsOK` プロパティは `true` に設定されます。**\[キャンセル\]** ボタンをクリックした場合は `false` に設定されます。  
  
 **\[OK\]** ボタンをクリックした場合、ハンドラーはコンテナー クラスから [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照を取得します。  その後、関連する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ プロパティが保持するユーザー情報を収集し、静的コントロールを使用して親ウィンドウに情報を表示します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ データは、マネージ文字列の形式であるため、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コントロールによってマーシャリングする必要があります。  **\[キャンセル\]** ボタンがクリックされた場合、ハンドラーは、スタティック コントロールからのデータをクリアします。  
  
 アプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] には、ユーザーが [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツの背景色を変更できるようにするラジオ ボタンのセット、および複数のフォント関連のプロパティが用意されています。  次の例は、アプリケーションのウィンドウ プロシージャ \(WndProc\)、および背景色など、各種のメッセージに対してさまざまなプロパティを設定するそのプロシージャのメッセージ処理からの抜粋です。  その他は類似しているため、示していません。  詳細とコンテキストについては、完全なサンプルを参照してください。  
  
 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]  
  
 背景色を設定するには、`WPFPageHost` から [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ \(`hostedPage`\) への参照を取得して、背景色のプロパティを適切な色に設定します。  サンプルでは、元の色、明るい緑、または明るいサーモン色の 3 つの色のオプションを使用します。  元の背景色は静的フィールドとして `WPFPageHost` クラスに格納されます。  他の 2 つの色を設定するには、新しい <xref:System.Windows.Media.SolidColorBrush> オブジェクトを作成して、<xref:System.Windows.Media.Colors> オブジェクトからコンストラクターに静的な色の値を渡します。  
  
<a name="implementing_the_wpf_page"></a>   
## WPF ページの実装  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは、実際の実装の知識がなくてもホストして、使用できます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツが個別の [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] にパッケージ化されていた場合は、いずれの [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 言語で構築できました。  以下は、このサンプルで使用する [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] の実装の簡単なチュートリアルです。  このセクションには、次のサブセクションが含まれています。  
  
<a name="autoNestedSectionsOUTLINE2"></a>   
-   [レイアウト](#page_layout)  
  
-   [データをホスト ウィンドウに返す](#returning_data_to_window)  
  
-   [WPF のプロパティを設定する](#set_page_properties)  
  
<a name="page_layout"></a>   
### レイアウト  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素は、5 つの <xref:System.Windows.Controls.TextBox> コントロールと、関連する <xref:System.Windows.Controls.Label> コントロール \(名前、住所、市区町村、都道府県、および郵便番号\) で構成しています。  さらに、**\[OK\]** と **\[キャンセル\]** という 2 つの <xref:System.Windows.Controls.Button> コントロールがあります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは `WPFPage` クラスに実装されています。  レイアウトは、<xref:System.Windows.Controls.Grid> レイアウト要素で処理されます。  クラスは <xref:System.Windows.Controls.Grid> から継承されます。これにより、クラスは効果的に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのルート要素になります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのコンストラクターは、必要な幅と高さを指定し、それに合わせて <xref:System.Windows.Controls.Grid> のサイズを指定します。  その後、コンストラクターは、<xref:System.Windows.Controls.ColumnDefinition> オブジェクトと <xref:System.Windows.Controls.RowDefinition> オブジェクトのセットを作成してから、それらを <xref:System.Windows.Controls.Grid> オブジェクトの基本の <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> および <xref:System.Windows.Controls.Grid.RowDefinitions%2A> コレクションにそれぞれ追加することで、基本のレイアウトを定義します。  これにより、5 つの行と、7 つの列のグリッドが定義され、セルの内容によって大きさが決定します。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]  
  
 次に、コンストラクターは [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を <xref:System.Windows.Controls.Grid> に追加します。  最初の要素はタイトルのテキストです。これは、グリッドの 1 行目の中央に表示される <xref:System.Windows.Controls.Label> コントロールです。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]  
  
 次の行には、名前の <xref:System.Windows.Controls.Label> コントロールと関連する <xref:System.Windows.Controls.TextBox> コントロールが格納されます。  ラベルとテキスト ボックスの各ペアに同じコードが使用されるため、コードはプライベート メソッドのペアに配置され、5 つのラベルとテキスト ボックスのペアすべてに使用されます。  メソッドは適切な制御を作成し、<xref:System.Windows.Controls.Grid> クラスの静的な <xref:System.Windows.Controls.Grid.SetColumn%2A> および <xref:System.Windows.Controls.Grid.SetRow%2A> メソッドを呼び出して、適切なセルにコントロールを配置します。  コントロールが作成されると、サンプルは <xref:System.Windows.Controls.Grid> の <xref:System.Windows.Controls.Panel.Children%2A> プロパティの <xref:System.Windows.Controls.UIElementCollection.Add%2A> メソッドを呼び出して、グリッドにコントロールを追加します。  残りのラベルとテキスト ボックスのペアを追加するコードは似ています。  詳細については、サンプル コードを参照してください。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]  
  
 2 つのメソッドの実装は、次のとおりです。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]  
  
 最後に、サンプルでは **\[OK\]** ボタンと **\[キャンセル\]** ボタンが追加され、<xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントにイベント ハンドラーがアタッチされます。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]  
  
<a name="returning_data_to_window"></a>   
### データをホスト ウィンドウに返す  
 いずれかのボタンをクリックすると、その <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントが発生します。  ホスト ウィンドウはこれらのイベントにハンドラーをアタッチして、<xref:System.Windows.Controls.TextBox> コントロールから直接データを取得します。  サンプルは、いくぶん直接的ではない方法を使用します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ内で <xref:System.Windows.Controls.Primitives.ButtonBase.Click> が処理され、カスタム イベント `OnButtonClicked` が生成されて、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツに通知されます。  これにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツがホストに通知する前にパラメーターの検証を実行します。  ハンドラーは、<xref:System.Windows.Controls.TextBox> コントロールからテキストを取得し、パブリック プロパティに割り当てます。ここからホストは情報を取得します。  
  
 WPFPage.h でのイベント宣言:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]  
  
 WPFPage.cpp での <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラー:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]  
  
<a name="set_page_properties"></a>   
### WPF のプロパティを設定する  
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ホストでは、ユーザーがいくつかの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのプロパティを変更できるようにします。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 側では、これはプロパティの変更の問題にすぎません。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のコンテンツ クラスの実装はいくらか複雑になります。これは、全コントロールのフォントを制御する 1 つのグローバル プロパティがないためです。  代わりに、各コントロールの適切なプロパティは、プロパティの set アクセサーで変更されます。  次の例は、`DefaultFontFamily` プロパティのコードを示しています。  プロパティを設定すると、プライベート メソッドが呼び出され、さまざまなコントロールに <xref:System.Windows.Controls.Control.FontFamily%2A> プロパティが設定されます。  
  
 WPFPage.h から:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]  
  
 WPFPage.cpp から:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]  
  
## 参照  
 <xref:System.Windows.Interop.HwndSource>   
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)