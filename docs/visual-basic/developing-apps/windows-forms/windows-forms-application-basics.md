---
title: Windows フォーム アプリケーションの基礎 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aaa7fbd679eceea53a673646173dc14dc4f209bc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="windows-forms-application-basics-visual-basic"></a>Windows フォーム アプリケーションの基礎 (Visual Basic)
Visual Basic の重要な部分は、ユーザーのコンピューターでローカルに実行する Windows フォーム アプリケーションを作成する機能です。 Visual Studio を使用して、Windows フォームを使用して、アプリケーションとユーザー インターフェイスを作成することができます。 Windows フォーム アプリケーションからのクラスをベースに構築、<xref:System.Windows.Forms>名前空間。  
  
## <a name="designing-windows-forms-applications"></a>設計の Windows フォーム アプリケーション  
 Windows フォームと Windows サービス アプリケーションを作成することができます[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]です。 詳細については、次のトピックを参照してください。  
  
-   [Windows フォームの概要](../../../framework/winforms/getting-started-with-windows-forms.md)です。 作成し、Windows フォームをプログラミングする方法についてを説明します。  
   
-   [Windows フォーム コントロール](../../../framework/winforms/controls/index.md)です。 Windows フォーム コントロールの使用の詳細を示すトピックのコレクションです。  
  
-   [Windows サービス アプリケーション](../../../framework/windows-services/index.md)です。 Windows サービスを作成する方法を説明するトピックを一覧表示します。  
  
## <a name="building-rich-interactive-user-interfaces"></a>リッチで対話型のユーザー インターフェイスの構築  
 Windows フォームのスマート クライアント コンポーネントは、 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]、読み取りと書き込み、ファイル システムなど、アプリケーションの一般的なタスクを有効にするマネージ ライブラリのセット。 などの開発環境を使用して[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]、ネットワーク経由でをリモート コンピューターで情報を表示したり、ユーザーから入力を要求、通信する Windows フォーム アプリケーションを作成することができます。  
  
 Windows フォームでは、フォームは、ユーザーに情報を表示しているビジュアル サーフェイスです。 通常、Windows フォーム アプリケーションをビルドするには、コントロールをフォームに配置し、マウスのクリックやキーの押下などのユーザー アクションへの応答を開発します。 "*コントロール*" は、データを表示したりデータ入力を受け入れたりする独立したユーザー インターフェイス (UI) 要素です。  
  
### <a name="events"></a>イベント  
 ユーザーがフォームまたはコントロールのコントロールのいずれかに対して、イベントが生成されます。 アプリケーションは、コードを使用してこれらのイベントに反応し、イベントが発生したときにそのイベントを処理します。 詳細については、「[Windows フォーム内でのイベント ハンドラーの作成](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)」を参照してください。  
  
### <a name="controls"></a>コントロール  
 Windows フォームには、さまざまなフォームに配置できるコントロールが含まれています。 テキスト ボックス、ボタン、ドロップダウン リスト ボックス、ラジオ ボタン、および Web ページを表示するコントロール。 フォーム上で使用できるすべてのコントロールの一覧については、「[Windows フォームで使用するコントロール](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md)」を参照してください。 既存のコントロールがニーズを満たしていない場合に、Windows フォームは <xref:System.Windows.Forms.UserControl> クラスを使用した独自のカスタム コントロールの作成もサポートしています。  
  
 Windows フォームには、Microsoft Office のようなハイエンド アプリケーションの機能をエミュレートする豊富な UI コントロールが用意されています。 使用して、<xref:System.Windows.Forms.ToolStrip>と<xref:System.Windows.Forms.MenuStrip>コントロール、ツールバーとメニュー テキストとイメージを含む、サブメニューを表示および他のコントロールのテキスト ボックスやコンボ ボックスなどのホストを作成できます。  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]ドラッグ アンド ドロップのフォーム デザイナーで、Windows フォーム アプリケーションに簡単に作成できます: だけをカーソルでコントロールを選択し、フォームの希望の位置に配置します。 デザイナーは、グリッド線や「スナップ線」などのツールを提供するコントロールの調整が備わっており、簡単にします。 かどうかを使用して[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]またはコンパイル、コマンドラインで使用することができます、 <xref:System.Windows.Forms.FlowLayoutPanel>、<xref:System.Windows.Forms.TableLayoutPanel>と<xref:System.Windows.Forms.SplitContainer>高度なを作成するコントロールが最小限の時間と労力でレイアウトを形成します。  
  
### <a name="custom-ui-elements"></a>カスタムの UI 要素  
 最後に、独自のカスタム UI 要素を作成する必要がある場合、<xref:System.Drawing>名前空間には、すべての線、円、およびその他の図形をフォーム上に直接表示する必要があります。 クラスが含まれています。  
  
 これらの機能の使用に関する詳細な手順については、次のヘルプ トピックを参照してください。  
  
|終了|解決方法については、|  
|--------|---------|  
|使用して新しい Windows フォーム アプリケーションを作成します。 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]|[チュートリアル: 簡単な Windows フォームの作成](http://msdn.microsoft.com/library/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|フォーム上のコントロールを使用します。|[方法: Windows フォームにコントロールを追加する](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|   
|使用してグラフィックスを作成します。 <xref:System.Drawing>|[グラフィックス プログラミングについて](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|カスタム コントロールを作成します。|[方法: UserControl クラスを継承する](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
## <a name="displaying-and-manipulating-data"></a>データの表示と操作  
 多くのアプリケーションは、データベース、XML ファイル、XML Web サービス、またはその他のデータ ソースからデータを表示する必要があります。 Windows フォームと呼ばれる、柔軟に制御を提供する、<xref:System.Windows.Forms.DataGridView>のすべてのデータが独自のセルを占有するので、このような従来の行と列の形式で表形式のデータを表示するためのコントロールです。 使用して<xref:System.Windows.Forms.DataGridView>個々 のセルの外観をカスタマイズ、任意の行と列のロックおよびその他の機能のセルの内部の複雑なコントロールを表示できます。  
  
 ネットワーク経由のデータ ソースへの接続は、Windows フォームのスマート クライアントを使用すればシンプルなタスクです。 <xref:System.Windows.Forms.BindingSource> コンポーネントは、[!INCLUDE[vsprvslong](~/includes/vsprvslong-md.md)] と [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] の新しい Windows フォームであり、データ ソースへの接続を表し、データをコントロールにバインドするためのメソッドの公開、前または次のレコードへの移動、レコードの編集、元のソースへの変更の保存を実行します。 <xref:System.Windows.Forms.BindingNavigator> コントロールは、ユーザーがレコード間を移動する <xref:System.Windows.Forms.BindingSource> コンポーネントに対して、シンプルなインターフェイスを提供します。  
  
### <a name="data-bound-controls"></a>データ バインド コントロール  
 プロジェクトのデータベース、Web サービス、およびオブジェクトなどのデータ ソースを表示するデータ ソース ウィンドウを使用して簡単にデータ バインド コントロールを作成することができます。 このウィンドウからプロジェクトのフォームに項目をドラッグして、データ バインド コントロールを作成できます。 また、[データ ソース] ウィンドウから既存のコントロールにオブジェクトをドラッグして、データに既存のコントロールをバインドすることもできます。  
  
### <a name="settings"></a>設定  
 別の種類のデータ バインド Windows フォームで管理できるは、設定です。 ほとんどのスマート クライアント アプリケーションは必要があります、フォームの前回のサイズなど、実行時状態に関する情報を保持し、保存されたファイルの既定の場所などのユーザー設定のデータを保持します。 アプリケーション設定機能クライアント コンピューターに両方の種類の設定を保存する簡単な方法を提供することによってこれらの要件に対応します。 いずれかを使用して 1 回定義[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]またはコード エディターでは、これらの設定を XML として永続化され、自動的に実行時にメモリに読み込まです。  
  
 これらの機能の使用に関する詳細な手順については、次のヘルプ トピックを参照してください。  
  
|終了|解決方法については、|  
|--------|---------|  
|使用して、<xref:System.Windows.Forms.BindingSource>コンポーネント|[方法: デザイナーを使用して Windows フォーム コントロールを BindingSource コンポーネントにバインドする](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|扱う[!INCLUDE[vstecado](~/includes/vstecado-md.md)]データ ソース|[方法: Windows フォーム BindingSource コンポーネントで ADO.NET データを並べ替える/フィルター処理する](https://msdn.microsoft.com/library/ya3sah92.aspx)|  
|データ ソース ウィンドウを使用します。|[チュートリアル: Windows フォームでのデータの表示](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>クライアント コンピューターにアプリケーションを配置する  
 アプリケーションを記述したとする必要がありますに送信するユーザーをインストールして、独自のクライアント コンピューターで実行できるようにします。 使用して、[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]テクノロジ、内からアプリケーションを配置できる[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]して数回のクリックを使用して、Web 上のアプリケーションを指す URL をユーザーに提供します。 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] すべての要素と、アプリケーション内の依存関係を管理し、クライアント コンピューターで、アプリケーションが正しくインストールされていることを確認します。  
  
 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] アプリケーションは、ユーザーがネットワークに接続されている場合にのみ実行するか、オンラインとオフラインの両方で実行するかを構成することができます。 アプリケーションがオフラインの操作をサポートするように指定するときに[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]のユーザーのアプリケーションへのリンクを追加**開始**] メニューの [できるように、ユーザーを使用すると、URL を使用しても開くことができます。  
  
 アプリケーションを更新するときに、新しい配置マニフェストとアプリケーションの新しいコピーを Web サーバーに発行します。 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 存在することが検出で更新が提供し、ユーザーのインストールのアップグレード古いアセンブリを更新する、カスタム プログラミングは必要ありません。  
  
 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] の概要については、「[ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)」を参照してください。 これらの機能の使用に関する詳細な手順については、次のヘルプ トピックを参照してください。  
  
|終了|解決方法については、|  
|--------|---------|  
|アプリケーションを展開します。 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [チュートリアル : ClickOnce アプリケーションを手動で配置する](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|更新プログラム、[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]展開|[方法 : ClickOnce アプリケーションの更新プログラムを管理する](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|セキュリティを管理します。 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[方法 : ClickOnce のセキュリティ設定を有効にする](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>その他のコントロールおよび機能  
 Windows フォームには、ダイアログ ボックスの作成、ヘルプやドキュメントの印刷や追加、アプリケーションの複数言語へのローカライズのサポートなど、一般的なタスクを高速で簡単に実装できる機能が他にも多数あります。 さらに、Windows フォームは、の堅牢なセキュリティ システムに依存しています。、 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]、より安全なアプリケーションを顧客にリリースできるようにします。  
  
 これらの機能の使用に関する詳細な手順については、次のヘルプ トピックを参照してください。  
  
|終了|解決方法については、|  
|--------|---------|  
|フォームの内容を印刷します。|[方法: Windows フォームでグラフィックスを印刷する](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [方法 : Windows フォームで複数ページのテキスト ファイルを印刷する](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|   
|Windows フォームのセキュリティについての詳細|[Windows フォームのセキュリティの概要](../../../framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 [Windows フォームの概要](../../../framework/winforms/windows-forms-overview.md)  
 [My.Forms オブジェクト](../../../visual-basic/language-reference/objects/my-forms-object.md)
