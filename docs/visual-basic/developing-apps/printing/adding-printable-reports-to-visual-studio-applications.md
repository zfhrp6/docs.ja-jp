---
title: Visual Studio アプリケーションへの印刷可能なレポートの追加
ms.date: 07/20/2015
helpviewer_keywords:
- printing [Visual Studio], reports
- reports [Visual Basic], printing in Visual Studio
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
ms.openlocfilehash: 4a7275a665e0c3290c2b3cd55c1af0c7cf0504f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592055"
---
# <a name="adding-printable-reports-to-visual-studio-applications"></a>Visual Studio アプリケーションへの印刷可能なレポートの追加
Visual Studio では、さまざまな豊富なデータを Visual Basic アプリケーションにレポートを追加するためのレポート ソリューションをサポートしています。 作成し、ReportViewer コントロール、Crystal Reports、または SQL Server Reporting Services を使用してレポートを追加できます。  
  
> [!NOTE]
>  SQL Server Reporting Services は、Visual Studio ではなく、SQL Server 2005 の一部です。 Reporting Services が SQL Server 2005 をインストールしていない限り、システムにインストールされていません。  
  
## <a name="overview-of-microsoft-reporting-technology-in-visual-basic-applications"></a>Visual Basic アプリケーションで Microsoft レポート テクノロジの概要  
 Microsoft レポート アプリケーションでのテクノロジを使用する、次の方法から選択します。  
  
-   Visual Basic Windows アプリケーションに ReportViewer コントロールの 1 つまたは複数のインスタンスを追加します。  
  
-   レポート サーバー Web サービスを呼び出すことにより、SQL Server Reporting Services をプログラムで統合します。  
  
-   ReportViewer コントロールと Microsoft SQL Server 2005 Reporting Services 一緒に使用、レポート プロセッサとしてコントロールをレポート ビューアーとレポート サーバーとして使用します。 (、レポート サーバーと ReportViewer コントロールを一緒に使用する場合は、SQL Server 2005 バージョンの Reporting Services を使用する必要がありますに注意してください。)  
  
## <a name="using-reportviewer-controls"></a>ReportViewer コントロールを使用します。  
 Visual Basic Windows アプリケーションにレポート機能を埋め込むには最も簡単な方法は、ReportViewer コントロールをアプリケーションのフォームに追加するのにです。 コントロールは、処理機能をアプリケーションに直接レポートを追加し、統合されたレポート デザイナーを提供し、任意の ADO.NET データ オブジェクトからデータを使用してレポートを作成できるようにします。 全機能を備えた API では、コントロールにプログラムからアクセスし、実行時の機能を構成することができるようにを報告します。  
  
 ReportViewer は、組み込みのレポート処理および表示、自由に配布できる単一のデータ コントロール内の機能を提供します。 次のレポート機能を必要とする場合、レポート ビューアー コントロールを選択します。  
  
-   レポート クライアント アプリケーションで処理します。 コントロールによって提供される、表示領域で、処理されたレポートが表示されます。  
  
-   ADO.NET データ テーブルにデータ バインディング。 使用するレポートを作成することができます<xref:System.Data.DataTable>インスタンス コントロールを提供します。 ビジネス オブジェクトに直接バインドすることもできます。  
  
-   アプリケーションに含めることができる再頒布可能パッケージを制御します。  
  
-   ページ ナビゲーション、印刷、検索、およびエクスポート形式などのランタイム機能。 ReportViewer ツールバーは、これらの操作のサポートを提供します。  
  
 ReportViewer コントロールを使用するドラッグしてから、**データ**Visual Basic Windows アプリケーションのフォーム上に Visual Studio ツールボックスのセクションです。  
  
### <a name="creating-reports-in-visual-studio-for-reportviewer-controls"></a>ReportViewer コントロール用の Visual Studio でレポートを作成します。  
 レポート ビューアーで実行されるレポートをビルドするには、追加、**レポート**プロジェクト テンプレート。 Visual Studio は、クライアント レポート定義 (.rdlc) ファイルを作成、ファイル、プロジェクトに追加し、Visual Studio ワークスペースに統合されたレポート デザイナーを開きます。  
  
 Visual Studio レポート デザイナーとの統合、**データソース**ウィンドウです。 フィールドをドラッグすると、**データソース**レポート、レポート デザイナーにウィンドウが、レポート定義ファイルにデータ ソースに関するメタデータをコピーします。 このメタデータは自動的にデータ バインド コードを生成する ReportViewer コントロールによって使用します。  
  
 Visual Studio レポート デザイナーでは、レポートのプレビュー機能は含まれません。 レポートをプレビューするには、アプリケーションを実行し、そこに埋め込まれたレポートをプレビューします。  
  
|基本的なレポート機能をアプリケーションに追加するには|  
|---|    
|1.ReportViewer コントロールをドラッグして、**データ**のタブ、**ツールボックス**フォーム上にします。<br />2.**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 **新しい項目の追加**ダイアログ ボックスで、**レポート**アイコンをクリックしてをクリックして**追加**です。<br />     レポート デザイナーで、開発環境が開きレポート (.rdlc) ファイルがプロジェクトに追加します。<br />3.レポート アイテムをドラッグして、**ツールボックス**レポート レイアウト上とするように配置します。<br />4.フィールドをドラッグ、**データソース**レポート レイアウトでのレポート アイテムにウィンドウです。|  
  
## <a name="using-reporting-services-in-visual-basic-applications"></a>Visual Basic アプリケーションでの Reporting Services の使用  
 Reporting Services は、SQL Server に含まれているサーバーに基づくレポート テクノロジです。 Reporting Services には、ReportViewer コントロールに記載されていないその他の機能が含まれます。 次の機能のいずれかが必要な場合は、Reporting Services を選択します。  
  
-   スケール アウト配置と複雑なまたは実行時間の長いレポートおよびの大量のレポートの利用状況、パフォーマンスの向上を提供するサーバー側のレポート処理。  
  
-   統合されたデータとレポート処理、カスタム レポート コントロールと豊富な出力形式のレンダリングをサポートします。  
  
-   レポートの実行時に正確に指定できるようにレポートの処理をスケジュールします。  
  
-   電子メールまたはファイル共有の場所に、分布をサブスクライバーに基づいたレポートです。  
  
-   アドホック レポートの必要に応じて、ビジネス ユーザーがレポートを作成できるようにします。  
  
-   データ ドリブン サブスクリプションで動的な受信者一覧にカスタマイズされたレポート出力をルーティングします。  
  
-   データ処理、レポートの配信、カスタム認証、およびレポートの表示用のカスタム拡張機能です。  
  
 レポート サーバーは、Web サービスとして実装されます。 アプリケーション コードでは、レポートやその他のメタデータにアクセスする Web サービスへの呼び出しを含める必要があります。 Web サービスでは、レポート サーバー インスタンスに完全なプログラムによるアクセスを提供します。  
  
 Reporting Services は Web ベースのレポート テクノロジであるため、既定のビューアーは HTML 形式で表示されるレポートを示します。 既定のレポートの表示形式として HTML を使用しないようにする場合は、アプリケーションのカスタム レポート ビューアーを記述する必要があります。  
  
### <a name="creating-reports-in-visual-studio-for-reporting-services"></a>Reporting Services 用の Visual Studio でレポートを作成します。  
 レポート サーバーで実行されるレポートをビルドするには、作成するレポート定義 (.rdl) ファイル、Business Intelligence Development Studio での Visual Studio で SQL Server 2005 に含まれています。  
  
> [!NOTE]
>  SQL Server Reporting Services と Business Intelligence Development Studio を使用するためにインストールされている SQL Server 2005 が必要です。  
  
 Business Intelligence Development Studio では、SQL Server コンポーネントに固有のプロジェクト テンプレートを追加します。 レポートを作成するから選択できます、**レポート サーバー プロジェクト**または**レポート サーバー プロジェクト ウィザード**テンプレート。 データ ソース接続とデータ ソースの種類、SQL Server、Oracle、Analysis Services、XML、SQL Server Integration Services などのさまざまなクエリを指定することができます。 A**データ** タブで、**レイアウト** タブ、および**プレビュー**  タブを使用すると、データの定義、レポートのレイアウトを作成および同じワークスペースですべてのレポートをプレビューできます。  
  
 どちらのテクノロジでは、コントロール、またはレポート サーバー用に作成するレポート定義を再利用できます。  
  
|レポート サーバーで実行されているレポートを作成するには|  
|---|    
|1.**ファイル**] メニューの [選択**新規**です。<br />     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。<br />2.**プロジェクトの種類** ウィンドウで、をクリックして**ビジネス インテリジェンス プロジェクト**です。<br />3.[テンプレート] ペインで選択**レポート サーバー プロジェクト**または**レポート サーバー プロジェクト ウィザード**です。|  
  
## <a name="using-reportviewer-controls-and-sql-server-reporting-services-together"></a>ReportViewer コントロールおよび SQL Server Reporting Services を一緒に使用  
 ReportViewer コントロールと SQL Server 2005 Reporting Services は、同じアプリケーション内に使用することができます。  
  
-   ReportViewer コントロールは、アプリケーションでレポートを表示するために使用するビューアーを提供します。  
  
-   Reporting Services レポートを提供し、リモート サーバー上のすべての処理を実行します。  
  
 リモートの Reporting Services レポート サーバーに保存され、処理されるレポートを表示するのには、ReportViewer コントロールを構成できます。 この種類の構成と呼びます*リモート処理モード*です。 リモート処理モードでは、コントロールは、リモートのレポート サーバーに格納されているレポートを要求します。 レポート サーバーは、すべてのレポートの処理、データ処理、およびレポートの表示を実行します。 終了、レンダリングされたレポートは、コントロールに返され、ビュー領域に表示されます。  
  
 その他のレポート サーバーのサポートで実行されるレポート エクスポート形式、別のレポートのパラメーター化の実装にロールベースの承認モデルを介してアクセスおよびレポート サーバーによってサポートされるデータ ソースの種類を使用して、レポート サーバー。  
  
 リモート処理モードを使用するには、ReportViewer コントロールを構成するときに、URL とサーバーのレポートへのパスを指定します。
