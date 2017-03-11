---
title: "Windows Forms Application Basics (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Windows applications"
  - "Windows Forms, Visual Basic"
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Windows Forms Application Basics (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の重要な要素に、ユーザーのコンピューター上でローカルに動作する Windows フォーム アプリケーションを作成する機能があります。  Windows フォームを使用するアプリケーションおよびユーザー インターフェイスを作成するために Visual Studio を使用できます。  Windows フォーム アプリケーションは、<xref:System.Windows.Forms> 名前空間のクラスを基に作成します。  
  
## Windows フォーム アプリケーションのデザイン  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] では、Windows フォーム アプリケーションと Windows サービス アプリケーションを作成できます。  詳細については、次のトピックを参照してください。  
  
-   [Windows フォームについて](../Topic/Getting%20Started%20with%20Windows%20Forms.md).  Windows フォームを作成およびプログラミングする方法についての情報です。  
  
-   [Windows Forms Walkthroughs](http://msdn.microsoft.com/ja-jp/fd44d13d-4733-416f-aefc-32592e59e5d9).  Windows フォームをベースとした、一般的に作成される Windows フォーム アプリケーションについて、詳細な開発手順を提供するトピックの一覧を示します。  
  
-   [Windows フォーム コントロール](../Topic/Windows%20Forms%20Controls.md).  Windows フォーム コントロールの使用について詳細に説明したトピックを集めたものです。  
  
-   [Windows Service Applications](../Topic/Developing%20Windows%20Service%20Applications.md).  Windows サービスの作成方法を説明するトピックの一覧を示します。  
  
## 充実した対話形式のユーザー インターフェイスの構築  
 Windows フォームは、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] のスマート クライアント コンポーネントであり、ファイル システムへの読み書きなど、共通のアプリケーション タスクを実現するマネージ ライブラリの集まりです。  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] などの開発環境を使用して、情報の表示、ユーザーに対する入力要求、ネットワーク経由でのリモート コンピューターとの通信を実行する Windows フォーム アプリケーションを作成できます。  
  
 Windows フォームでいうフォームとは、ユーザーに対して情報を表示する外観部分の土台のことです。  Windows フォーム アプリケーションの作成では、フォーム上にコントロールを配置し、ユーザー アクション \(マウスのクリックやキーの押下など\) に対する応答を開発するという方法が一般的です。  *コントロール*とは、データの表示やデータ入力の受け付けを行う、個別のユーザー インターフェイス \(UI\) 要素です。  
  
### イベント  
 フォームまたはその上のコントロールに対してユーザーが操作を行うと、イベントが生成されます。  アプリケーションでは、こうしたイベントに応答するためのコードを使用して、イベントの発生時に処理を行います。  詳細については、「[Windows フォーム内でのイベント ハンドラーの作成](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)」を参照してください。  
  
### コントロール  
 Windows フォームにはさまざまなコントロールが用意されており、フォーム上に配置できます。たとえば、テキスト ボックス、ボタン、ドロップダウン ボックス、オプション ボタンを表示するコントロールがあるのに加え、Web ページを表示するコントロールもあります。  フォーム上で使用できるすべてのコントロールの一覧については、「[Windows フォームで使用するコントロール](../Topic/Controls%20to%20Use%20on%20Windows%20Forms.md)」を参照してください。  Windows フォームでは、既存のコントロールでニーズに対応できない場合には、<xref:System.Windows.Forms.UserControl> クラスを使用して独自のカスタム コントロールを作成することもできます。  
  
 Windows フォームには、Microsoft Office のようなハイエンド アプリケーションの機能をエミュレートする、豊富な UI コントロールが用意されています。  <xref:System.Windows.Forms.ToolStrip> コントロールおよび <xref:System.Windows.Forms.MenuStrip> コントロールを使用すると、テキストおよびイメージを含むツール バーやメニューの作成、サブメニューの表示、および他のコントロール \(テキスト ボックスやコンボ ボックスなど\) のホストが可能です。  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] のドラッグ アンド ドロップ フォーム デザイナーを使用すると、Windows フォーム アプリケーションを簡単に作成できます。コントロールをポインターで選択し、フォーム上の目的の位置に配置するだけです。  このデザイナーには、グリッド線や "スナップ線" などのツールが備わっており、コントロールの配置で苦労する必要がありません。  また、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] を使用する場合でも、コマンド ラインでコンパイルする場合でも、<xref:System.Windows.Forms.FlowLayoutPanel>、<xref:System.Windows.Forms.TableLayoutPanel>、および <xref:System.Windows.Forms.SplitContainer> の各コントロールを使用して、最小限の時間と労力で高度なフォーム レイアウトを作成できます。  
  
### カスタムの UI 要素  
 独自のカスタム UI 要素を作成する必要がある場合には、線、円、およびその他の形状をフォーム上に直接描画するために必要なすべてのクラスが、<xref:System.Drawing> 名前空間に含まれています。  
  
 これらの機能の使用手順の詳細については、以下のヘルプ トピックを参照してください。  
  
|目的|参照項目|  
|--------|----------|  
|[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] で Windows フォーム アプリケーションを新規作成する。|[Walkthrough: Creating a Simple Windows Form](http://msdn.microsoft.com/ja-jp/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|フォーム上でコントロールを使用する。|[方法 : Windows フォームにコントロールを追加する](../Topic/How%20to:%20Add%20Controls%20to%20Windows%20Forms.md)|  
|フォームおよびそのコントロールからのイベントを処理する。|[How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/ja-jp/8461e9b8-14e8-406f-936e-3726732b23d2)|  
|<xref:System.Windows.Forms.ToolStrip> コントロールを使用する。|[方法 : デザイナーを使用して標準アイテムで基本的な ToolStrip を作成する](../Topic/How%20to:%20Create%20a%20Basic%20Windows%20Forms%20ToolStrip%20with%20Standard%20Items%20Using%20the%20Designer.md)|  
|<xref:System.Drawing> でグラフィックスを作成する。|[グラフィックス プログラミングについて](../Topic/Getting%20Started%20with%20Graphics%20Programming.md)|  
|カスタム コントロールを作成する。|[方法 : UserControl クラスを継承する](../Topic/How%20to:%20Inherit%20from%20the%20UserControl%20Class.md)|  
  
## データの表示と操作  
 多くのアプリケーションでは、データベース、XML ファイル、XML Web サービス、およびその他のデータ ソースのデータを表示する必要があります。  Windows フォームには、<xref:System.Windows.Forms.DataGridView> コントロールという柔軟なコントロールが用意されています。このコントロールでは、行と列から成る従来型の表形式のデータを表示でき、データの各項目を、それぞれ別個のセルに配置できます。  <xref:System.Windows.Forms.DataGridView> にはさまざまな機能があります。個々のセルの表示形式のカスタマイズ、任意の行や列のロック、セル内での複合コントロールの表示などです。  
  
 Windows フォームのスマート クライアントでは、ネットワーク経由でのデータ ソースへの接続も簡単です。  [!INCLUDE[vsprvslong](../../../csharp/misc/includes/vsprvslong-md.md)] および [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong-md.md)] の Windows フォームの新機能である <xref:System.Windows.Forms.BindingSource> コンポーネントは、データ ソースへの接続を表し、コントロールへのデータのバインド、前のレコードや次のレコードへの移動、レコードの編集、元のソースへの変更の保存などを実行するためのメソッドを公開します。  <xref:System.Windows.Forms.BindingNavigator> コントロールは、<xref:System.Windows.Forms.BindingSource> コンポーネントの簡単なインターフェイスとなるもので、ユーザーがレコード間を移動できます。  
  
### データ バインド コントロール  
 \[データ ソース\] ウィンドウを使用して、データ バインド コントロールを簡単に作成できます。このウィンドウには、データベース、Web サービス、プロジェクト内のオブジェクトなどのデータ ソースが表示されます。  このウィンドウからプロジェクト内のフォームに項目をドラッグすると、データ バインド コントロールを作成できます。  また、\[データ ソース\] ウィンドウから既存のコントロールにオブジェクトをドラッグするという方法でも、既存のコントロールをデータにバインドできます。  
  
### 設定  
 Windows フォームでは、設定もデータ バインディングの一種として管理できます。  大半のスマート クライアント アプリケーションでは、実行時の状態 \(前回のフォームのサイズなど\) についての情報や、ユーザー設定のデータ \(保存するファイルの既定の場所など\) を保持しておく必要があります。  アプリケーション設定機能では、両方の種類の設定をクライアント コンピューターに格納するための簡単な方法が用意されており、これらの要件に対応できます。  これらの設定は、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] またはコード エディターを使用して定義すると、XML として保持され、実行時に自動的にメモリに読み込まれます。  
  
 これらの機能の使用手順の詳細については、以下のヘルプ トピックを参照してください。  
  
|目的|参照項目|  
|--------|----------|  
|<xref:System.Windows.Forms.BindingSource> コンポーネントを使用する。|[方法 : デザイナーを使用して Windows フォーム コントロールを BindingSource コンポーネントにバインドする](../Topic/How%20to:%20Bind%20Windows%20Forms%20Controls%20with%20the%20BindingSource%20Component%20Using%20the%20Designer.md)|  
|[!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] データ ソースを操作する。|[方法 : Windows フォーム BindingSource コンポーネントで ADO.NET データを並べ替える\/フィルター処理する](../Topic/How%20to:%20Sort%20and%20Filter%20ADO.NET%20Data%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)|  
|\[データ ソース\] ウィンドウを使用する。|[チュートリアル: Windows フォームでのデータの表示](../Topic/Walkthrough:%20Displaying%20Data%20on%20a%20Windows%20Form.md)|  
|アプリケーション設定を使用する。|[How to: Create Application Settings Using the Designer](http://msdn.microsoft.com/ja-jp/53b3af80-1c02-4e35-99c6-787663148945)|  
  
## クライアント コンピューターへのアプリケーションの配置  
 アプリケーションを作成したら、ユーザーに送る必要があります。各自のクライアント コンピューターにインストールして実行してもらうためです。  [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] テクノロジを使用すると、数回のクリック操作だけで、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] からアプリケーションを配置でき、Web 上でのアプリケーションの場所を示す URL をユーザーに伝えることができます。  [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] は、アプリケーション内のすべての要素と依存関係を管理し、アプリケーションがクライアント コンピューターに適切にインストールされるようにします。  
  
 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] アプリケーションは、ユーザーがネットワークに接続しているときにのみ動作するように設定することも、オンラインでもオフラインでも動作するように設定することもできます。  アプリケーションがオフライン操作をサポートするように指定した場合、[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] は、ユーザーが URL を使用しなくてもアプリケーションを開けるように、ユーザーの **\[スタート\]** メニューに当該アプリケーションへのリンクを追加します。  
  
 アプリケーションを更新するときには、新しい配置マニフェストと、アプリケーションの新しいコピーを Web サーバーに対して発行します。  [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] は、利用可能な更新があることを検出し、ユーザーのインストール内容をアップグレードします。古いアセンブリを更新するためのカスタム プログラミングは不要です。  
  
 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] の詳細については、「[ClickOnce のセキュリティと配置](/visual-studio/deployment/clickonce-security-and-deployment)」を参照してください。  これらの機能の使用手順の詳細については、以下のヘルプ トピックを参照してください。  
  
|目的|参照項目|  
|--------|----------|  
|[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] でアプリケーションを配置する|[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)<br /><br /> [チュートリアル : ClickOnce アプリケーションを手動で配置する](../Topic/Walkthrough:%20Manually%20Deploying%20a%20ClickOnce%20Application.md)|  
|[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 配置を更新する|[方法 : ClickOnce アプリケーションの更新プログラムを管理する](../Topic/How%20to:%20Manage%20Updates%20for%20a%20ClickOnce%20Application.md)|  
|[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] でセキュリティを管理する|[方法 : ClickOnce のセキュリティ設定を有効にする](../Topic/How%20to:%20Enable%20ClickOnce%20Security%20Settings.md)|  
  
## 他のコントロールと機能  
 Windows フォームには、共通のタスクをすばやく簡単に実装するための機能が、他にもたくさんあります。ダイアログ ボックスの作成、印刷、ヘルプおよびドキュメントの追加、複数言語へのアプリケーションのローカライズのサポートなどです。  また、Windows フォームは、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] の堅牢なセキュリティ システムを基盤としているため、より安全性の高いアプリケーションを顧客にリリースできます。  
  
 これらの機能の使用手順の詳細については、以下のヘルプ トピックを参照してください。  
  
|目的|参照項目|  
|--------|----------|  
|フォームの内容を印刷する。|[方法 : Windows フォームでグラフィックスを印刷する](../Topic/How%20to:%20Print%20Graphics%20in%20Windows%20Forms.md)<br /><br /> [方法 : Windows フォームで複数ページのテキスト ファイルを印刷する](../Topic/How%20to:%20Print%20a%20Multi-Page%20Text%20File%20in%20Windows%20Forms.md)|  
|Windows フォーム アプリケーションをグローバル化する。|[Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/ja-jp/9a96220d-a19b-4de0-9f48-01e5d82679e5)|  
|Windows フォームのセキュリティについて理解を深める。|[Windows フォームのセキュリティの概要](../Topic/Security%20in%20Windows%20Forms%20Overview.md)|  
  
## 参照  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Windows フォームの概要](../Topic/Windows%20Forms%20Overview.md)   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)