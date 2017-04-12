---
title: "Windows フォーム アプリケーションの基礎 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8275d3c06ebd89254a07127b4850d32ef0580830
ms.lasthandoff: 03/13/2017

---
# <a name="windows-forms-application-basics-visual-basic"></a>Windows フォーム アプリケーションの基礎 (Visual Basic)
重要な部分[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ユーザーのコンピューターでローカルに実行する Windows フォーム アプリケーションを作成する機能です。 Visual Studio を使用して、Windows フォームを使用してアプリケーションおよびユーザー インターフェイスを作成することができます。 クラスの Windows フォーム アプリケーションを構築、<xref:System.Windows.Forms>名前空間</xref:System.Windows.Forms>。  
  
## <a name="designing-windows-forms-applications"></a>設計の Windows フォーム アプリケーション  
 Windows フォームおよび使用して Windows サービス アプリケーションを作成する[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]です。 詳細については、次のトピックを参照してください。  
  
-   [Windows フォームの概要](https://msdn.microsoft.com/library/ms229601.aspx)します。 作成し、Windows フォームをプログラミングする方法についてを説明します。  
   
-   [Windows フォーム コントロールの](https://msdn.microsoft.com/library/ettb6e2a.aspx)です。 Windows フォーム コントロールの使用の詳細を示すトピックのコレクションです。  
  
-   [Windows サービス アプリケーション](https://msdn.microsoft.com/library/y817hyb6.aspx)します。 Windows サービスを作成する方法を説明するトピックを一覧表示します。  
  
## <a name="building-rich-interactive-user-interfaces"></a>リッチで対話型のユーザー インターフェイスの構築  
 Windows フォームのスマート クライアント コンポーネントは、 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]、読み取りと書き込みをファイル システムなどの一般的なアプリケーション タスクを実現するマネージ ライブラリのセットです。 などの開発環境を使用して[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]、ネットワーク経由でリモート コンピューターと情報を表示して、ユーザーからの入力を要求し、通信する Windows フォーム アプリケーションを作成することができます。  
  
 Windows フォームでは、フォームをユーザーに情報を表示するビジュアル サーフェイスです。 通常、Windows フォーム アプリケーションをビルドするには、コントロールをフォームに配置し、マウス クリックやキーの押下などのユーザー アクションに対する応答を開発します。 A*コントロール*データを表示したりデータ入力を受け入れたりする独立したユーザー インターフェイス (UI) 要素です。  
  
### <a name="events"></a>イベント  
 ユーザーがフォームやそのコントロールに対して、イベントが生成されます。 アプリケーションは、コードを使用してこれらのイベントに反応し、イベントが発生したときにそのイベントを処理します。 詳細については、次を参照してください。 [Windows フォームでのイベント ハンドラーの作成](https://msdn.microsoft.com/library/dacysss4.aspx)します。  
  
### <a name="controls"></a>コントロール  
 Windows フォームには、さまざまなフォーム上に配置できるコントロールが含まれています。 テキスト ボックス、ボタン、ドロップダウン ボックス、ラジオ ボタン、および Web ページを表示するコントロール。 フォーム上で使用できるすべてのコントロールの一覧は、次を参照してください。 [Windows フォームで使用するコントロール](https://msdn.microsoft.com/library/3xdhey7w.aspx)します。 既存のコントロールがニーズに合わない場合は、Windows フォームもサポート<xref:System.Windows.Forms.UserControl>クラス</xref:System.Windows.Forms.UserControl>を使用して、独自のカスタム コントロールの作成  
  
 Windows フォームには、Microsoft Office のようなハイエンド アプリケーションの機能をエミュレートする豊富な UI コントロールが用意されています。 使用して、<xref:System.Windows.Forms.ToolStrip>と<xref:System.Windows.Forms.MenuStrip>コントロール、ツールバーとメニュー テキストとイメージを含む、サブメニューの表示、テキスト ボックスやコンボ ボックスなどの他のコントロールをホストするを作成できます</xref:System.Windows.Forms.MenuStrip></xref:System.Windows.Forms.ToolStrip>。  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]ドラッグ アンド ドロップ フォーム デザイナーで、Windows フォーム アプリケーションに簡単に作成できます。 だけをカーソルでコントロールを選択して、フォームの希望の位置に配置します。 デザイナーがグリッド線や「スナップ線」などのツールを提供するので、コントロールを配置します。 使用するかどうか[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]またはコンパイル、コマンドラインで使用することができます、 <xref:System.Windows.Forms.FlowLayoutPanel>、<xref:System.Windows.Forms.TableLayoutPanel>と<xref:System.Windows.Forms.SplitContainer>コントロールを作成、高度なフォームを最小限の時間と労力のレイアウト</xref:System.Windows.Forms.SplitContainer></xref:System.Windows.Forms.TableLayoutPanel></xref:System.Windows.Forms.FlowLayoutPanel>。  
  
### <a name="custom-ui-elements"></a>カスタム UI 要素  
 最後に、独自のカスタム UI 要素を作成する必要がある場合、<xref:System.Drawing>名前空間には、すべての線、円、およびその他の図形をフォーム上に直接表示する必要がありますクラスが含まれています。</xref:System.Drawing> 。  
  
 これらの機能を使用する手順については、次のヘルプ トピックを参照してください。  
  
|目的|参照トピック|  
|--------|---------|  
|新しい Windows フォーム アプリケーションを作成します。[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]|[チュートリアル: 単純な Windows フォームの作成](http://msdn.microsoft.com/en-us/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|フォーム上のコントロールを使用します。|[方法: Windows フォームにコントロールを追加](https://msdn.microsoft.com/library/0h5y8567.aspx)|   
|使用してグラフィックスを作成します。<xref:System.Drawing></xref:System.Drawing>|[グラフィックス プログラミングの概要](https://msdn.microsoft.com/library/da0f23z7.aspx)|  
|カスタム コントロールを作成します。|[方法: UserControl クラスを継承](https://msdn.microsoft.com/library/00ctb4z0.aspx)|  
  
## <a name="displaying-and-manipulating-data"></a>データの表示と操作  
 多くのアプリケーションは、データベース、XML ファイル、XML Web サービス、またはその他のデータ ソースからデータを表示する必要があります。 Windows フォームは、柔軟なコントロールと呼ばれる、<xref:System.Windows.Forms.DataGridView>のすべてのデータが独自のセルを占有するので、従来の行と列の形式でこのような表形式のデータを表示するためのコントロール</xref:System.Windows.Forms.DataGridView>。 使用して<xref:System.Windows.Forms.DataGridView>個々 のセルの外観をカスタマイズ、任意の行と列のロックおよびその他の機能の&1; つのセルの内部の複雑なコントロールを表示することができます</xref:System.Windows.Forms.DataGridView>。  
  
 ネットワーク経由のデータ ソースへの接続は、Windows フォームのスマート クライアントを使用すればシンプルなタスクです。 <xref:System.Windows.Forms.BindingSource>コンポーネントは、新しい Windows フォームで[!INCLUDE[vsprvslong](../../../csharp/misc/includes/vsprvslong_md.md)]と[!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)]データ ソースへの接続を表し、前後のレコードへの移動、レコードの編集、および変更を元のソースに保存しているコントロールへのデータ バインディングのメソッドを公開します</xref:System.Windows.Forms.BindingSource>。 <xref:System.Windows.Forms.BindingNavigator>コントロールでは、上の単純なインターフェイスが用意されています、<xref:System.Windows.Forms.BindingSource>コンポーネントに対してユーザーがレコード間を移動します</xref:System.Windows.Forms.BindingSource></xref:System.Windows.Forms.BindingNavigator>。  
  
### <a name="data-bound-controls"></a>データ バインド コントロール  
 プロジェクトのデータベース、Web サービス、およびオブジェクトなどのデータ ソースを表示するデータ ソース ウィンドウを使用して簡単にデータ バインド コントロールを作成することができます。 このウィンドウからプロジェクトのフォームに項目をドラッグして、データ バインド コントロールを作成できます。 また、[データ ソース] ウィンドウから既存のコントロールにオブジェクトをドラッグして、データに既存のコントロールをバインドすることもできます。  
  
### <a name="settings"></a>設定  
 別の種類のデータ バインド Windows フォームで管理できるは、設定です。 ほとんどのスマート クライアント アプリケーションはフォームの前回のサイズなどの実行時の状態に関する情報を保持する必要があり、保存されたファイルの既定の場所などのユーザー設定データを保持します。 アプリケーション設定機能は、クライアント コンピューターに両方の種類の設定を保存する簡単な方法を提供することにより、これらの要件を対応します。 いずれかを使用して定義した後[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]またはコード エディターでは、これらの設定は XML として永続化され、自動的に実行時にメモリに読み込まします。  
  
 これらの機能を使用する手順については、次のヘルプ トピックを参照してください。  
  
|目的|参照トピック|  
|--------|---------|  
|<xref:System.Windows.Forms.BindingSource>コンポーネント</xref:System.Windows.Forms.BindingSource>を使用してください。|[方法: Windows フォーム コントロールを BindingSource コンポーネント デザイナーを使用してバインド](https://msdn.microsoft.com/library/801dxw2t.aspx)|  
|扱う[!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]データ ソース|[方法: Windows フォーム BindingSource コンポーネントで ADO.NET データをフィルター処理の並べ替えと](https://msdn.microsoft.com/library/ya3sah92.aspx)|  
|データ ソース ウィンドウを使用します。|[チュートリアル: Windows フォームでのデータの表示](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>クライアント コンピューターにアプリケーションを配置する  
 アプリケーションを作成するとする必要がありますに送信するユーザーをインストールして、独自のクライアント コンピューターに実行できるようにします。 使用して、[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]テクノロジ、内からアプリケーションを配置できる[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]で、数回クリックして、Web 上のアプリケーションを指す URL をユーザーに提供します。 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]すべての要素と、アプリケーション内の依存関係を管理し、アプリケーションがクライアント コンピューターに正しくインストールされていることを確認します。  
  
 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] アプリケーションは、ユーザーがネットワークに接続されている場合にのみ実行するか、オンラインとオフラインの両方で実行するかを構成することができます。 アプリケーションがオフラインの操作をサポートするように指定すると[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]、ユーザーのアプリケーションへのリンクを追加**開始**] メニューの [できるように、ユーザーを使用すると、URL を使用しても開くことができます。  
  
 アプリケーションを更新するときに、新しい配置マニフェストとアプリケーションの新しいコピーを Web サーバーに発行します。 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]検出、更新プログラムは、ユーザーのインストールをアップグレード古いアセンブリを更新するは、カスタム プログラミングは必要ありません。  
  
 完全な概要について[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]を参照してください[ClickOnce のセキュリティと配置](https://docs.microsoft.com/visualstudio/deployment/clickonce-security-and-deployment)します。 これらの機能を使用する手順については、次のヘルプ トピックを参照してください。  
  
|目的|参照トピック|  
|--------|---------|  
|使用したアプリケーションを展開します。[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]|[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](https://docs.microsoft.com/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [チュートリアル : ClickOnce アプリケーションを手動で配置する](https://docs.microsoft.com/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|更新プログラム、[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]展開|[方法 : ClickOnce アプリケーションの更新プログラムを管理する](https://docs.microsoft.com/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|セキュリティと管理します。[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]|[方法 : ClickOnce のセキュリティ設定を有効にする](https://docs.microsoft.com/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>その他のコントロールおよび機能  
 Windows フォームには、ダイアログ ボックスの作成、ヘルプやドキュメントの印刷や追加、アプリケーションの複数言語へのローカライズのサポートなど、一般的なタスクを高速で簡単に実装できる機能が他にも多数あります。 さらに、Windows フォームの堅牢なセキュリティ システムに依存している、 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]、顧客により安全なアプリケーションをリリースすることが可能です。  
  
 これらの機能を使用する手順については、次のヘルプ トピックを参照してください。  
  
|目的|参照トピック|  
|--------|---------|  
|フォームの内容を印刷します。|[方法: Windows フォームでグラフィックスを印刷](https://msdn.microsoft.com/library/741a0ktc.aspx)<br /><br /> [方法: Windows フォームで複数ページのテキスト ファイルを印刷](https://msdn.microsoft.com/library/cwbe712d.aspx)|   
|Windows フォームのセキュリティについての詳細|[セキュリティの Windows フォームの概要](https://msdn.microsoft.com/library/90k49ccb.aspx)|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Windows フォームの概要](https://msdn.microsoft.com/library/8bxxy49h.aspx)   
 [My.Forms オブジェクト](../../../visual-basic/language-reference/objects/my-forms-object.md)
