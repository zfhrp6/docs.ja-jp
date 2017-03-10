---
title: "チュートリアル : DataRepeater コントロールでのデータの表示 (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, チュートリアル"
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# チュートリアル : DataRepeater コントロールでのデータの表示 (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このチュートリアルでは、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールにバインドされたデータを表示する基本的なシナリオ全体を示します。  
  
## 必須コンポーネント  
 このチュートリアルには、Northwind サンプル データベースが必要です。  
  
 開発用コンピューターにこのデータベースがない場合は、[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088)からダウンロードできます。 手順については、「[Downloading Sample Databases](../Topic/Downloading%20Sample%20Databases.md)」を参照してください。  
  
## 概要  
 このチュートリアルの前半部分は、次の 4 つの主要なタスクについて説明します。  
  
-   ソリューションを作成する。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを追加する。  
  
-   データ ソースを追加する。  
  
-   データ バインドされたコントロールを追加する。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
## DataRepeater ソリューションの作成  
 最初に、プロジェクトとソリューションを作成します。  
  
#### DataRepeater ソリューションを作成するには  
  
1.  Visual Studio で **\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの **\[プロジェクトの種類\]** ペインで、**\[Visual Basic\]** を展開し、**\[Windows\]** をクリックします。  
  
3.  **\[テンプレート\]** ペインの **\[Windows フォーム アプリケーション\]** をクリックします。  
  
4.  **\[名前\]** ボックスに「`DataRepeaterApp`」と入力します。  
  
5.  **\[OK\]** をクリックします。  
  
     Windows フォーム デザイナーが開きます。  
  
6.  Windows フォーム デザイナーでフォームを選択します。**\[プロパティ\]** ウィンドウで、**Size** プロパティを `800, 700` に設定します。  
  
## DataRepeater コントロールの追加  
 この手順では、フォームに <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを追加します。  
  
#### DataRepeater コントロールを追加するには  
  
1.  **\[表示\]** メニューの **\[ツールボックス\]** をクリックします。  
  
     **ツールボックス**が表示されます。  
  
2.  **\[Visual Basic PowerPacks\]** タブを選択します。  
  
3.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを **Form1** にドラッグします。  
  
4.  \[プロパティ\] ウィンドウで、**Location** プロパティを `0, 25` に設定します。  
  
5.  **Size** プロパティを `460, 600` に設定します。  
  
## データ ソースの追加  
 この手順では、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールのデータ ソースを追加します。  
  
#### データ ソースを追加するには  
  
1.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  
  
2.  **\[データ ソース\]** ウィンドウで、**\[新しいデータ ソースの追加\]** をクリックします。  
  
3.  **\[データソースの種類を選択\]** ページで、**\[データベース\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  **\[データ接続の選択\]** ページで、次のいずれかの操作を行います。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は、これをクリックします。  
  
         または  
  
    -   **\[新しい接続\]** をクリックし、新しいデータ接続を構成します。 詳細については、「[How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/ja-jp/360c340d-e5a6-4a7e-a569-e95d500be43d)」を参照してください。  
  
5.  データベースにパスワードが必要な場合は、該当するオプションを選択して重要情報を含め、**\[次へ\]** をクリックします。  
  
    > [!NOTE]
    >  ダイアログ ボックスが表示された場合は、**\[はい\]** をクリックしてファイルをプロジェクトに保存します。  
  
6.  **\[アプリケーション構成ファイルに接続文字列を保存\]** ページで、**\[次へ\]** をクリックします。  
  
7.  **\[データベース オブジェクトの選択\]** ページの **\[テーブル\]** ノードを展開します。  
  
8.  **Customers** テーブルと **Orders** テーブルの横のチェック ボックスをオンにし、**\[完了\]** をクリックします。  
  
     プロジェクトに **NorthwindDataSet** が追加され、**\[データ ソース\]** ウィンドウに **Customers** テーブルと **Orders** テーブルが表示されます。  
  
## データ バインドされたコントロールの追加  
 この手順では、データ バインドされたコントロールを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> に追加します。  
  
#### データ バインディング コントロールを追加するには  
  
1.  **\[データ ソース\]** ウィンドウで、**Customers** テーブルの最上位ノードを選択します。  
  
2.  テーブル ノードのドロップダウン リストの **\[詳細\]** をクリックして、テーブルのドロップ タイプを **\[詳細\]** に変更します。  
  
3.  **\[Customers\]** テーブル ノードを選択し、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの項目テンプレート領域 \(上部領域\) にドラッグします。  
  
     フォームに <xref:System.Windows.Forms.BindingNavigator> コントロールが追加され、コンポーネント トレイに **NorthwindDataSet**、**CustomersBindingSource**、**CustomersTableAdapter**、**TableAdapterManager**、および **CustomersBindingNavigator** の各コンポーネントが追加されます。  
  
4.  すべてのフィールドとそれらに関連付けられているラベルを選択し、項目テンプレート領域の左端近くに配置します。  
  
5.  後半の 5 つのフィールド \(**Region**、**Postal Code**、**Country**、**Phone**、**Fax**\) とそれらに関連付けられているラベルを選択し、上へ移動して前半の 6 つのフィールドの右側に配置します。  
  
6.  項目テンプレート \(コントロールの上部領域\) を選択します。  
  
7.  \[プロパティ\] ウィンドウで、**Size** プロパティを `427, 170` に設定します。  
  
 この時点で、顧客の繰り返しの一覧が表示される作業アプリケーションが作成されました。 F5 キーを押してこのアプリケーションを実行し、データの変更、および顧客レコードの追加と削除を行うことができます。  
  
 次の省略可能な手順では、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールをカスタマイズする方法について説明します。  
  
## 次の手順 \(省略可能\)  
 このチュートリアルの後半部分は、次の 4 つの省略可能な手順で構成されています。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの外観を変更する。  
  
-   ユーザーがレコードを追加または削除できないようにする。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールに検索機能を追加する。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールにマスター\/詳細テーブルを追加する。  
  
## DataRepeater コントロールの外観を変更する  
 この省略可能な手順では、デザイン時に <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの `BackColor` を変更します。 また、行の色を交互にし、条件に応じてラベルの `ForeColor` を変更するコードを追加します。  
  
#### コントロールの外観を変更するには  
  
1.  Windows フォーム デザイナーで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールのメイン \(下部\) 領域を選択します。  
  
2.  \[プロパティ\] ウィンドウで、`BackColor` プロパティを白に設定します。  
  
3.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> をダブルクリックしてコード エディターを開きます。  
  
4.  コード エディターで、\[イベント\] ボックスの一覧の **\[DrawItem\]** をクリックします。  
  
5.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> イベント ハンドラーで、`BackColor` を交互にする次のコードを追加します。  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/DataRepeaterAppCS/DataRepeaterWalkthrough.cs#1)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/DataRepeaterApp/DataRepeaterWalkthrough.vb#1)]  
  
6.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> イベント ハンドラーで、条件に応じてラベルの `ForeColor` を変更する次のコードを追加します。  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/DataRepeaterAppCS/DataRepeaterWalkthrough.cs#2)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/DataRepeaterApp/DataRepeaterWalkthrough.vb#2)]  
  
7.  F5 キーを押してアプリケーションを実行し、カスタマイズを確認します。  
  
## ユーザーがレコードを追加または削除できないようにする  
 この省略可能な手順では、ユーザーが <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールでレコードを追加または削除できないようにするコードを追加します。  
  
#### ユーザーがレコードを追加または削除できないようにするには  
  
1.  Windows フォーム デザイナーで、フォームをダブルクリックしてコード エディターを開きます。  
  
2.  `Form_Load` イベントに次のコードを追加します。  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/DataRepeaterAppCS/DataRepeaterWalkthrough.cs#3)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/DataRepeaterApp/DataRepeaterWalkthrough.vb#3)]  
  
3.  \[クラス名\] ボックスの一覧で **\[BindingNavigatorDeleteItem\]** をクリックします。 \[メソッド名\] ボックスの一覧で **\[EnabledChanged\]** をクリックします。  
  
4.  `BindingNavigatorDeleteItem_EnabledChanged` イベント ハンドラーに次のコードを追加します。  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/DataRepeaterAppCS/DataRepeaterWalkthrough.cs#4)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/DataRepeaterApp/DataRepeaterWalkthrough.vb#4)]  
  
    > [!NOTE]
    >  この手順が必要なのは、現在のレコードが変更されるたびに <xref:System.Windows.Forms.BindingSource> によって **DeleteItem** ボタンが有効になるためです。  
  
5.  F5 キーを押してアプリケーションを実行します。**DeleteItem** ボタンが無効になっていて、Del キーを押しても項目を削除できないことを確認します。  
  
## DataRepeater コントロールに検索機能を追加する  
 この省略可能な手順では、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールで値を検索する機能を実装します。 検索文字列が見つかると、このコントロールはその値を含む項目を選択し、スクロールして表示します。  
  
#### 検索機能を追加するには  
  
1.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールが含まれるフォーム上に、**ツールボックス**から <xref:System.Windows.Forms.TextBox> コントロールをドラッグします。  
  
     それを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの下に配置します。  
  
2.  \[プロパティ\] ウィンドウで、**Name** プロパティを **SearchTextBox** に変更します。  
  
3.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールが含まれるフォーム上に、**ツールボックス**から <xref:System.Windows.Forms.Button> コントロールをドラッグします。 それを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの下に配置します。  
  
4.  \[プロパティ\] ウィンドウで、**Name** プロパティを **SearchButton** に変更します。**Text** プロパティを **Search** に変更します。  
  
5.  <xref:System.Windows.Forms.Button> コントロールをダブルクリックしてコード エディターを開き、`SearchButton_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/DataRepeaterAppCS/DataRepeaterWalkthrough.cs#5)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/DataRepeaterApp/DataRepeaterWalkthrough.vb#5)]  
  
6.  F5 キーを押してアプリケーションを実行します。**\[SearchTextBox\]** に顧客 ID を入力し、**\[Search\]** ボタンをクリックします。  
  
## DataRepeater にマスター\/詳細テーブルを追加する  
 この省略可能な手順では、顧客ごとに関連する注文を表示するために、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールをもう 1 つ追加します。  
  
#### マスター\/詳細テーブルを追加するには  
  
1.  **ツールボックス**の **\[Visual Basic PowerPacks\]** タブから <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールをもう 1 つ、フォーム上にドラッグします。  
  
2.  \[プロパティ\] ウィンドウで、**Location** プロパティを `465, 25` に設定します。  
  
3.  **Size** プロパティを `315, 600` に設定します。  
  
4.  **\[データ ソース\]** ウィンドウで、**\[Customers\]** テーブル ノードを展開し、**Orders** テーブルの詳細ノードを選択します。  
  
5.  この **Orders** テーブルのドロップ タイプを、テーブル ノードのドロップダウン リストの **\[詳細\]** をクリックして \[詳細\] に変更します。  
  
6.  この **\[Orders\]** テーブル ノードを 2 番目の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの項目テンプレート領域 \(上部領域\) にドラッグします。  
  
     **OrdersBindingSource** コンポーネントおよび **OrdersTableAdapter** コンポーネントがコンポーネント トレイに追加されます。  
  
7.  F5 キーを押してアプリケーションを実行します。 1 番目の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールで顧客を選択すると、2 番目の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールにその顧客の注文が表示されます。  
  
## 参照  
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)   
 [How to: Search Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [How to: Disable Adding and Deleting DataRepeater Items](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)