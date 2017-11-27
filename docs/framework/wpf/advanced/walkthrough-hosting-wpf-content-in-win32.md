---
title: "チュートリアル: Win32 での WPF コンテンツのホスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords: hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fce70ab1571602fb046d3ccde9e7c014834ae6a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>チュートリアル: Win32 での WPF コンテンツのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。 ただし、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] コードにかなりの投資がある場合は、元のコードを書き換えるより、アプリケーションに [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の機能を追加するほうがより効果的であることがあります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホストするための簡単なメカニズムを備えています[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]でコンテンツを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウです。  
  
 このチュートリアルはサンプル アプリケーションを記述する方法を説明[Win32 ウィンドウ サンプルでの WPF コンテンツをホストしている](http://go.microsoft.com/fwlink/?LinkID=160004)、そのホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]でコンテンツを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウです。 このサンプルを拡張すると、いずれの [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウでもホストできます。 マネージ コードとアンマネージ コードの混在が関係しているため、このアプリケーションは [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] で記述されます。  
  
 
  
<a name="requirements"></a>   
## <a name="requirements"></a>要件  
 このチュートリアルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プログラミングの基礎知識があることを前提としています。 基本的な概要については[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プログラミングを参照してください[作業の開始](../../../../docs/framework/wpf/getting-started/index.md)です。 概要については[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]プログラミングでは、参照してください、多数の書籍を受け、特に*プログラミング Windows* Charles Petzold でします。  
  
 このチュートリアルに付属するサンプルがで実装されているため[!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]、このチュートリアルの使用に関する知識を前提と[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]プログラムに、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]マネージ コード プログラミングの理解とします。 [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] の知識があることは、役立ちますが、必須ではありません。  
  
> [!NOTE]
>  このチュートリアルには、関連するサンプルからのコード例が多数含まれています。 しかし、読みやすくするため、完全なサンプル コードは含まれていません。 完全なサンプル コードを参照してください。 [Win32 ウィンドウ サンプルでは WPF のコンテンツをホストしている](http://go.microsoft.com/fwlink/?LinkID=160004)です。  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>基本手順  
 使用する基本的な手順を概説ホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]でコンテンツを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウです。 残りのセクションでは、各手順の詳細について説明します。  
  
 ホストしているにキー[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]上のコンテンツ、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウは、<xref:System.Windows.Interop.HwndSource>クラスです。 このクラスをラップ、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]でコンテンツを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]に組み込むことができるよう、ウィンドウ、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]子ウィンドウとして。 次の方法では、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] および [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を単一のアプリケーションに統合します。  
  
1.  実装して[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マネージ クラスとしてコンテンツ。  
  
2.  
          [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションを [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] で実装します。 既存のアプリケーションとアンマネージの [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] コードで使用を開始する場合、通常は、プロジェクトの設定を `/clr` コンパイラ フラグを含めるように変更して、マネージ コードを呼び出せるようにします。  
  
3.  スレッド処理モデルをシングル スレッド アパートメント (STA: Single Threaded Apartment) に設定します。  
  
4.  処理、 [WM_CREATE](http://msdn.microsoft.com/library/ms632619.aspx)ウィンドウ プロシージャと、次の操作で通知します。  
  
    1.  新しい <xref:System.Windows.Interop.HwndSource> オブジェクトを、親ウィンドウがその `parent` パラメーターとなるように指定して作成します。  
  
    2.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ クラスのインスタンスを作成します。  
  
    3.  参照を割り当てる、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ オブジェクトを<xref:System.Windows.Interop.HwndSource.RootVisual%2A>のプロパティ、<xref:System.Windows.Interop.HwndSource>です。  
  
    4.  コンテンツの HWND を取得します。 <xref:System.Windows.Interop.HwndSource.Handle%2A> オブジェクトの <xref:System.Windows.Interop.HwndSource> プロパティにウィンドウ ハンドル (HWND) が格納されます。 アプリケーションのアンマネージ部分で使用できる HWND を取得するには、`Handle.ToPointer()` を HWND にキャストします。  
  
5.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照を保持する静的フィールドを含むマネージ クラスを実装します。 このクラスを使用すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コードから [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コンテンツへの参照を取得できるようになります。  
  
6.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを静的フィールドに割り当てます。  
  
7.  通知を受信、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツを 1 つまたは複数のハンドラーをアタッチすることにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベント。  
  
8.  静的フィールドに格納した参照を使用して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツと通信し、プロパティの設定などを行います。  
  
> [!NOTE]
>  使用することも[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を実装する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。 ただし、このコンテンツは [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] として別にコンパイルしてから、その [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] に [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションから参照する必要があります。 手順の残りの部分は、前述の手順と同様です。  
  
<a name="implementing_the_application"></a>   
## <a name="implementing-the-host-application"></a>ホスト アプリケーションの実装  
 このセクションの説明をホストする方法[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]で基本的なコンテンツ[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]アプリケーションです。 コンテンツ自体は、マネージ クラスとして [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] に実装されます。 ほとんどの部分が、簡単な [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のプログラミングです。 コンテンツの実装の重要な側面は、後ほど[WPF コンテンツを実装する](#implementing_the_wpf_page)です。  
  
<a name="autoNestedSectionsOUTLINE1"></a>   
-   [基本的なアプリケーション](#the_basic_application)  
  
-   [WPF コンテンツのホスティング](#hosting_the_wpf_page)  
  
-   [WPF コンテンツへの参照の保持](#holding_a_reference)  
  
-   [WPF コンテンツとの通信](#communicating_with_the_page)  
  
<a name="the_basic_application"></a>   
### <a name="the-basic-application"></a>基本的なアプリケーション  
 ホスト アプリケーションの開始点は、[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] テンプレートを作成することでした。  
  
1.  開いている[!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)]を選択して**新しいプロジェクト**から、**ファイル**メニュー。  
  
2.  選択**Win32**の一覧から[!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)]プロジェクトの種類。 既定の言語がない場合[!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)]、下にあるこれらのプロジェクト タイプが見つかります**他の言語**します。  
  
3.  選択、 **Win32 プロジェクト**テンプレート、プロジェクトに名前を割り当てるし、をクリックして**OK**を起動する、 **Win32 アプリケーション ウィザード**です。  
  
4.  ウィザードの既定の設定をそのまま使用し、をクリックして**完了**プロジェクトを開始します。  
  
 このテンプレートは、次のような基本的な [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションを作成します。  
  
-   アプリケーションのエントリ ポイント。  
  
-   関連するウィンドウ プロシージャ (WndProc) を含むウィンドウ。  
  
-   使用するメニュー**ファイル**と**ヘルプ**見出し。 **ファイル**メニューがあります、**終了**項目をアプリケーションを終了します。 **ヘルプ**メニューがあります、**に関する**単純なダイアログ ボックスを起動する項目。  
  
 ホストにコードの記述を開始する前に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツのために必要な 2 つの基本的なテンプレートを変更します。  
  
 1 つ目は、プロジェクトをマネージ コードとしてコンパイルすることです。 既定では、プロジェクトはアンマネージ コードとしてコンパイルされます。 ただし、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] はマネージ コードで実装されているため、プロジェクトは状況に応じてコンパイルする必要があります。  
  
1.  プロジェクト名を右クリックして**ソリューション エクスプ ローラー**選択**プロパティ**を起動するコンテキスト メニューから、**プロパティ ページ** ダイアログ ボックス。  
  
2.  選択**構成プロパティ**左側のウィンドウで、ツリー ビューです。  
  
3.  選択**共通言語ランタイム**からのサポート、**プロジェクトの既定値**右ペインの一覧です。  
  
4.  選択**共通言語ランタイム サポート (/clr)**ドロップダウン リスト ボックスからです。  
  
> [!NOTE]
>  このコンパイラ フラグを使用すると、アプリケーションでマネージ コードを使用できますが、アンマネージ コードは以前と同様にコンパイルされます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、シングル スレッド アパートメント (STA) スレッド処理モデルを使用します。 適切に機能するために、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ コードは、する必要があります、アプリケーションのスレッド モデルを STA に設定、エントリ ポイントに属性を適用しています。  
  
 [!code-cpp[Win32HostingWPFPage#WinMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]  
  
<a name="hosting_the_wpf_page"></a>   
### <a name="hosting-the-wpf-content"></a>WPF コンテンツのホスティング  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツは、単純なアドレスのエントリのアプリケーションです。 それは、ユーザー名やアドレスなどを取得する複数の <xref:System.Windows.Controls.TextBox> コントロールで構成されています。 2 つ<xref:System.Windows.Controls.Button>コントロール、 **OK**と**キャンセル**です。 ユーザーがクリックしたとき**OK**、ボタンの<xref:System.Windows.Controls.Primitives.ButtonBase.Click>からデータを収集するイベント ハンドラー、<xref:System.Windows.Controls.TextBox>制御し、対応するプロパティに割り当てます、カスタム イベントを発生させます`OnButtonClicked`です。 ユーザーがクリックしたとき**キャンセル**、ハンドラーが単を発生させます`OnButtonClicked`です。 `OnButtonClicked` のイベント引数オブジェクトには、どのボタンをクリックしたかを示すブール型フィールドが含まれています。  
  
 ホストに、コード、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のハンドラーでコンテンツが実装されている、 [WM_CREATE](http://msdn.microsoft.com/library/ms632619.aspx)ホスト ウィンドウに通知します。  
  
 [!code-cpp[Win32HostingWPFPage#WMCreate](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]  
  
 `GetHwnd`メソッド サイズと位置情報、および親ウィンドウ ハンドルを受け取り、ホストのウィンドウ ハンドルを返します[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。  
  
> [!NOTE]
>  `#using` 名前空間に `System::Windows::Interop` ディレクティブを使用することはできません。 使用すると、その名前空間の <xref:System.Windows.Interop.MSG> 構造体と winuser.h で宣言した MSG 構造体の間で名前の競合が発生します。 代わりに、その名前空間のコンテンツにアクセスするための完全修飾名を使用する必要があります。  
  
 [!code-cpp[Win32HostingWPFPage#GetHwnd](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]  
  
 ホストすることはできません、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツを直接、アプリケーション ウィンドウです。 代わりに、まず <xref:System.Windows.Interop.HwndSource> コンテンツをラップするための [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] オブジェクトを作成します。 このオブジェクトをホストするように設計されたウィンドウで、基本的に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。 ホストする、<xref:System.Windows.Interop.HwndSource>オブジェクトの子として作成して親ウィンドウに、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウは、アプリケーションの一部であります。 <xref:System.Windows.Interop.HwndSource> コンストラクターのパラメーターには、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] の子ウィンドウの作成時に CreateWindow に渡される情報とほとんど同じ情報が含まれています。  
  
 次のインスタンスを作成する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ オブジェクト。 この場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは、`WPFPage` を使用して、別のクラス [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] として実装されます。 さらに、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で実装することもできます。 ただし、これを行う必要がありますを別のプロジェクトを設定して、ビルド、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツとして、[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]です。 プロジェクトにその [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] への参照を追加し、その参照を使用して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのインスタンスを作成します。  
  
 表示する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツへの参照を割り当てることによって、子ウィンドウで、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]へのコンテンツ、<xref:System.Windows.Interop.HwndSource.RootVisual%2A>のプロパティ、<xref:System.Windows.Interop.HwndSource>です。  
  
 次のコード行は、イベント ハンドラー `WPFButtonClicked` を [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツの `OnButtonClicked` イベントにアタッチしています。 ユーザーがクリックしたときに、このハンドラーが呼び出されます、 **[ok]**または**キャンセル**ボタンをクリックします。 参照してください[wpf コンテンツ](#communicating_with_the_page)このイベント ハンドラーの詳細についてはします。  
  
 示されているコードの最後の行は、<xref:System.Windows.Interop.HwndSource> オブジェクトに関連付けられているウィンドウ ハンドル (HWND) を返します。 このハンドルは、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コードから使用してホストされたウィンドウにメッセージを送信することができます。ただし、サンプルではこれはできません。 <xref:System.Windows.Interop.HwndSource> オブジェクトは、メッセージを受信するたびにイベントを発生させます。 メッセージを処理するには、<xref:System.Windows.Interop.HwndSource.AddHook%2A> メソッドを呼び出してメッセージ ハンドラーをアタッチしてから、そのハンドラーでメッセージを処理します。  
  
<a name="holding_a_reference"></a>   
### <a name="holding-a-reference-to-the-wpf-content"></a>WPF コンテンツへの参照の保持  
 多くのアプリケーションでは、後で [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツと通信することができます。 たとえば、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのプロパティを変更したり、場合によっては <xref:System.Windows.Interop.HwndSource> オブジェクトが異なる [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをホストするようにしたりできます。 そのためには、<xref:System.Windows.Interop.HwndSource> オブジェクトまたは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照が必要です。 <xref:System.Windows.Interop.HwndSource> オブジェクトと関連する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは、ウィンドウ ハンドルを破棄するまでメモリに残ります。 ただし、<xref:System.Windows.Interop.HwndSource> オブジェクトに割り当てる変数は、ウィンドウ プロシージャから戻ると同時にスコープの外に出ます。 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションでこの問題を処理するためによく使用される方法は、静的変数またはグローバル変数を使用することです。 残念ながら、このような変数の種類に対してマネージ オブジェクトを割り当てることはできません。 <xref:System.Windows.Interop.HwndSource> オブジェクトに関連付けられているウィンドウ ハンドルを、グローバル変数または静的変数に割り当てることができますが、オブジェクト自体にアクセスすることはできません。  
  
 この問題の最も簡単な解決法は、静的フィールドのセットを含むマネージ クラスを実装して、アクセスが必要なすべてのマネージ オブジェクトへの参照を保持することです。 サンプルでは、`WPFPageHost` クラスを使用して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照、および後でユーザーが変更する可能性があるプロパティの数の初期値を保持します。 これは、ヘッダーで定義します。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageHost](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]  
  
 `GetHwnd` 関数の後半部分では、後に、`myPage` がスコープ内にある間に使用するため、対象のフィールドに値を割り当てます。  
  
<a name="communicating_with_the_page"></a>   
### <a name="communicating-with-the-wpf-content"></a>WPF コンテンツとの通信  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツとの通信には次の 2 種類があります。 アプリケーションからの情報を受信する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツのユーザーがクリックしたときに、 **OK**または**キャンセル**ボタン。 アプリケーションには、背景色や既定のフォント サイズなどのさまざまな [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] コンテンツのプロパティをユーザーが変更できるようにする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] があります。  
  
 前述のように、ユーザーがいずれかのボタンをクリックすると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは `OnButtonClicked` イベントを発生させます。 アプリケーションは、これらの通知を受信するため、このイベントにハンドラーをアタッチします。 場合、 **OK** button がクリックしてされました、ハンドラーがからユーザー情報を取得、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツし、スタティック コントロールのセットに表示されます。  
  
 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]  
  
 ハンドラーは、カスタム イベント引数オブジェクトを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のコンテンツ、`MyPageEventArgs` から受信します。 オブジェクトの`IsOK`プロパティに設定されている`true`場合、 **[ok]**ボタンがクリックされたと`false`場合、**キャンセル**button がクリックしてされました。  
  
 場合、 **OK** button がクリックしてされました、ハンドラーがへの参照を取得、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテナー クラスからのコンテンツ。 その後、関連する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ プロパティが保持するユーザー情報を収集し、静的コントロールを使用して親ウィンドウに情報を表示します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ データは、マネージ文字列の形式であるため、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コントロールによってマーシャリングする必要があります。 場合、**キャンセル**button がクリックしてされました、ハンドラーがスタティック コントロールからのデータをクリアします。  
  
 アプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] には、ユーザーが [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツの背景色を変更できるようにするラジオ ボタンのセット、および複数のフォント関連のプロパティが用意されています。 次の例は、アプリケーションのウィンドウ プロシージャ (WndProc)、および背景色など、各種のメッセージに対してさまざまなプロパティを設定するそのプロシージャのメッセージ処理からの抜粋です。 その他は類似しているため、示していません。 詳細とコンテキストについては、完全なサンプルを参照してください。  
  
 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]  
  
 背景色を設定するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] から `hostedPage` コンテンツ (`WPFPageHost`) への参照を取得して、背景色のプロパティを適切な色に設定します。 サンプルでは、元の色、明るい緑、または明るいサーモン色の 3 つの色のオプションを使用します。 元の背景色は静的フィールドとして `WPFPageHost` クラスに格納されます。 他の 2 つの色を設定するには、新しい <xref:System.Windows.Media.SolidColorBrush> オブジェクトを作成して、<xref:System.Windows.Media.Colors> オブジェクトからコンストラクターに静的な色の値を渡します。  
  
<a name="implementing_the_wpf_page"></a>   
## <a name="implementing-the-wpf-page"></a>WPF ページの実装  
 ホストして、使用することができます、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ナレッジは、実際の実装のないコンテンツ。 場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]別個のコンテンツをパッケージ化されていた[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]、いずれかで作成されている可能性があります[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]言語です。 以下は、このサンプルで使用する [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] の実装の簡単なチュートリアルです。 このセクションには、次のサブセクションが含まれています。  
  
<a name="autoNestedSectionsOUTLINE2"></a>   
-   [レイアウト](#page_layout)  
  
-   [データをホスト ウィンドウに返す](#returning_data_to_window)  
  
-   [WPF のプロパティを設定する](#set_page_properties)  
  
<a name="page_layout"></a>   
### <a name="layout"></a>レイアウト  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]内の要素、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツから成る 5<xref:System.Windows.Controls.TextBox>コントロールで、関連付けられて<xref:System.Windows.Controls.Label>コントロール: 名前、アドレス、City、State、および Zip です。 2 つある<xref:System.Windows.Controls.Button>コントロール、 **OK**と**キャンセル**  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは `WPFPage` クラスに実装されています。 レイアウトは、<xref:System.Windows.Controls.Grid> レイアウト要素で処理されます。 クラスは <xref:System.Windows.Controls.Grid> から継承されます。これにより、クラスは効果的に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのルート要素になります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ コンス トラクターは、必要な幅と高さ、およびサイズ、<xref:System.Windows.Controls.Grid>それに従っています。 定義し、基本的なレイアウトのセットを作成することで<xref:System.Windows.Controls.ColumnDefinition>と<xref:System.Windows.Controls.RowDefinition>オブジェクトとに追加すること、<xref:System.Windows.Controls.Grid>基本オブジェクト<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>と<xref:System.Windows.Controls.Grid.RowDefinitions%2A>コレクション、それぞれします。 これにより、5 つの行と、7 つの列のグリッドが定義され、セルの内容によって大きさが決定します。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]  
  
 次に、コンストラクターは [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を <xref:System.Windows.Controls.Grid> に追加します。 最初の要素はタイトルのテキストです。これは、グリッドの 1 行目の中央に表示される <xref:System.Windows.Controls.Label> コントロールです。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]  
  
 次の行には、名前の <xref:System.Windows.Controls.Label> コントロールと関連する <xref:System.Windows.Controls.TextBox> コントロールが格納されます。 ラベルとテキスト ボックスの各ペアに同じコードが使用されるため、コードはプライベート メソッドのペアに配置され、5 つのラベルとテキスト ボックスのペアすべてに使用されます。 メソッドは適切な制御を作成し、<xref:System.Windows.Controls.Grid> クラスの静的な <xref:System.Windows.Controls.Grid.SetColumn%2A> および <xref:System.Windows.Controls.Grid.SetRow%2A> メソッドを呼び出して、適切なセルにコントロールを配置します。 コントロールが作成されると、サンプルは <xref:System.Windows.Controls.UIElementCollection.Add%2A> の <xref:System.Windows.Controls.Panel.Children%2A> プロパティの <xref:System.Windows.Controls.Grid> メソッドを呼び出して、グリッドにコントロールを追加します。 残りのラベルとテキスト ボックスのペアを追加するコードは似ています。 詳細については、サンプル コードを参照してください。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]  
  
 2 つのメソッドの実装は、次のとおりです。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]  
  
 最後に、サンプルを追加、 **[ok]**と**キャンセル**にイベント ハンドラーをアタッチして、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]  
  
<a name="returning_data_to_window"></a>   
### <a name="returning-the-data-to-the-host-window"></a>データをホスト ウィンドウに返す  
 いずれかのボタンをクリックすると、その <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントが発生します。 ホスト ウィンドウはこれらのイベントにハンドラーをアタッチして、<xref:System.Windows.Controls.TextBox> コントロールから直接データを取得します。 サンプルは、いくぶん直接的ではない方法を使用します。 処理、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>内で、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ、およびカスタム イベントを発生`OnButtonClicked`に通知する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。 これにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をホストに通知する前にいくつかのパラメーター検証を行うにはコンテンツ。 ハンドラーは、<xref:System.Windows.Controls.TextBox> コントロールからテキストを取得し、パブリック プロパティに割り当てます。ここからホストは情報を取得します。  
  
 WPFPage.h でのイベント宣言:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]  
  
 WPFPage.cpp での <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラー:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]  
  
<a name="set_page_properties"></a>   
### <a name="setting-the-wpf-properties"></a>WPF のプロパティを設定する  
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ホストにより、ユーザーがいくつか変更[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツのプロパティです。 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 側では、これはプロパティの変更の問題にすぎません。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のコンテンツ クラスの実装はいくらか複雑になります。これは、全コントロールのフォントを制御する 1 つのグローバル プロパティがないためです。 代わりに、各コントロールの適切なプロパティは、プロパティの set アクセサーで変更されます。 次の例のコードを示しています、`DefaultFontFamily`プロパティです。 プロパティを設定すると、プライベート メソッドが呼び出され、さまざまなコントロールに <xref:System.Windows.Controls.Control.FontFamily%2A> プロパティが設定されます。  
  
 WPFPage.h から:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]  
  
 WPFPage.cpp から:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Interop.HwndSource>  
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
