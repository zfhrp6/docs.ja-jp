---
title: "チュートリアル: DataRepeater コントロール (Visual Studio) でのデータの表示 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 09f15c94c3d5a3387935c8d3f4758c0ecfd7cfcd
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a>チュートリアル : DataRepeater コントロールでのデータの表示 (Visual Studio)
このチュートリアルでは、基本的な開始から終了までにバインドされたデータを表示するため、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
## <a name="prerequisite"></a>必須コンポーネント  
 このチュートリアルには、Northwind サンプル データベースが必要です。  
  
 開発用コンピューターにこのデータベースがない場合は、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088)からダウンロードできます。 手順については、次を参照してください。[サンプル データベースのダウンロード](https://msdn.microsoft.com/library/bb399411)します。  
  
## <a name="overview"></a>概要  
 このチュートリアルの前半部分は、次の&4; つの主要なタスクについて説明します。  
  
-   ソリューションを作成する。  
  
-   追加する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
-   データ ソースを追加する。  
  
-   データ バインドされたコントロールを追加する。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a>DataRepeater ソリューションの作成  
 最初に、プロジェクトとソリューションを作成します。  
  
#### <a name="to-create-a-datarepeater-solution"></a>DataRepeater ソリューションを作成するには  
  
1.  Visual Studio で **[ファイル]** メニューの **[新しいプロジェクト]**をクリックします。  
  
2.  **[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Visual Basic]**を展開し、 **[Windows]**をクリックします。  
  
3.  **[テンプレート]** ペインの **[Windows フォーム アプリケーション]**をクリックします。  
  
4.  **[名前]** ボックスに「 `DataRepeaterApp`」と入力します。  
  
5.  **[OK]**をクリックします。  
  
     Windows フォーム デザイナーが開きます。  
  
6.  Windows フォーム デザイナーでフォームを選択します。 **[プロパティ]** ウィンドウで、 **Size** プロパティを `800, 700`に設定します。  
  
## <a name="adding-a-datarepeater-control"></a>DataRepeater コントロールの追加  
 この手順で追加、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールをフォーム</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
#### <a name="to-add-a-datarepeater-control"></a>DataRepeater コントロールを追加するには  
  
1.  **[表示]** メニューの **[ツールボックス]**をクリックします。  
  
     **ツールボックス** が表示されます。  
  
2.  **[Visual Basic PowerPacks]** タブを選択します。  
  
3.  ドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールを**Form1**</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 。  
  
4.  [プロパティ] ウィンドウで、 **Location** プロパティを `0, 25`に設定します。  
  
5.  **Size** プロパティを `460, 600`に設定します。  
  
## <a name="adding-a-data-source"></a>データ ソースの追加  
 このステップでのデータ ソースを追加する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
#### <a name="to-add-a-data-source"></a>データ ソースを追加するには  
  
1.  **[データ]** メニューの **[データ ソースの表示]**をクリックします。  
  
2.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]**をクリックします。  
  
3.  **[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]**をクリックします。  
  
4.  **[データ接続の選択]** ページで、次のいずれかの操作を行います。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は、これをクリックします。  
  
         または  
  
    -   **[新しい接続]** をクリックし、新しいデータ接続を構成します。 詳細については、次を参照してください。[方法: SQL Server データベースへの接続を作成する](http://msdn.microsoft.com/en-us/360c340d-e5a6-4a7e-a569-e95d500be43d)です。  
  
5.  データベースにパスワードが必要な場合は、該当するオプションを選択して重要情報を含め、 **[次へ]**をクリックします。  
  
    > [!NOTE]
    >  ダイアログ ボックスが表示された場合は、 **[はい]** をクリックしてファイルをプロジェクトに保存します。  
  
6.  **[アプリケーション構成ファイルに接続文字列を保存]** ページで、 **[次へ]** をクリックします。  
  
7.  **[データベース オブジェクトの選択]** ページの **[テーブル]** ノードを展開します。  
  
8.  **Customers** テーブルと **Orders** テーブルの横のチェック ボックスをオンにし、 **[完了]**をクリックします。  
  
     プロジェクトに**NorthwindDataSet** が追加され、 **[データ ソース]** ウィンドウに **Customers** テーブルと **Orders** テーブルが表示されます。  
  
## <a name="adding-data-bound-controls"></a>データ バインドされたコントロールの追加  
 この手順で<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>データ バインド コントロールを追加します。  
  
#### <a name="to-add-data-bound-controls"></a>データ バインディング コントロールを追加するには  
  
1.  **[データ ソース]** ウィンドウで、 **Customers** テーブルの最上位ノードを選択します。  
  
2.  テーブル ノードのドロップダウン リストの **[詳細]** をクリックして、テーブルのドロップ タイプを **[詳細]** に変更します。  
  
3.  選択、**顧客**ノードにテーブルが表示され、項目テンプレート (上の領域) の領域にドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
     A<xref:System.Windows.Forms.BindingNavigator>コントロールがフォームに追加され、 **NorthwindDataSet**、 **CustomersBindingSource**、 **CustomersTableAdapter**、 **TableAdapterManager**、および**CustomersBindingNavigator**のコンポーネントがコンポーネント トレイに追加されます</xref:System.Windows.Forms.BindingNavigator>。  
  
4.  すべてのフィールドとそれらに関連付けられているラベルを選択し、項目テンプレート領域の左端近くに配置します。  
  
5.  後半の&5; つのフィールド (**Region**、 **Postal Code**、 **Country**、 **Phone**、 **Fax**) とそれらに関連付けられているラベルを選択し、上へ移動して前半の&6; つのフィールドの右側に配置します。  
  
6.  項目テンプレート (コントロールの上部領域) を選択します。  
  
7.  [プロパティ] ウィンドウで、 **Size** プロパティを `427, 170`に設定します。  
  
 この時点で、顧客の繰り返しの一覧が表示される作業アプリケーションが作成されました。 F5 キーを押してこのアプリケーションを実行し、データの変更、および顧客レコードの追加と削除を行うことができます。  
  
 次の省略可能な手順では、カスタマイズする方法を説明します、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
## <a name="next-steps-optional"></a>次の手順 (省略可能)  
 このチュートリアルの後半部分は、次の&4; つの省略可能な手順で構成されています。  
  
-   外観の変更、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
-   ユーザーがレコードを追加または削除できないようにする。  
  
-   検索機能を追加する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
-   マスター/詳細テーブルを追加、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a>DataRepeater コントロールの外観を変更する  
 このオプションの手順で変更する、`BackColor`の<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールをデザイン時</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 また、行の色を交互にし、条件に応じてラベルの `ForeColor` を変更するコードを追加します。  
  
#### <a name="to-change-the-appearance-of-the-control"></a>コントロールの外観を変更するには  
  
1.  Windows フォーム デザイナーでのメインの (下部) の領域を選択して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
2.  [プロパティ] ウィンドウで、 `BackColor` プロパティを白に設定します。  
  
3.  ダブルクリックして、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コード エディターを開きます</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
4.  コード エディターで、[イベント] ボックスの一覧の **[DrawItem]**をクリックします。  
  
5.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>イベント ハンドラーを交互に使用する次のコードを追加、 `BackColor`:</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>イベント ハンドラーを変更するには、次のコードを追加、`ForeColor`条件に応じてラベルの:</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  F5 キーを押してアプリケーションを実行し、カスタマイズを確認します。  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a>ユーザーがレコードを追加または削除できないようにする  
 この省略可能な手順は、ユーザーが追加または内のレコードを削除できないようにするコードを追加、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a>ユーザーがレコードを追加または削除できないようにするには  
  
1.  Windows フォーム デザイナーで、フォームをダブルクリックしてコード エディターを開きます。  
  
2.  `Form_Load` イベントに次のコードを追加します。  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  [クラス名] ボックスの一覧で **[BindingNavigatorDeleteItem]**をクリックします。 [メソッド名] ボックスの一覧で **[EnabledChanged]**をクリックします。  
  
4.  `BindingNavigatorDeleteItem_EnabledChanged` イベント ハンドラーに次のコードを追加します。  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  この手順は必要なため、<xref:System.Windows.Forms.BindingSource>有効にするには、 **DeleteItem**現在のレコードが変更されるたびにボタンをクリックします</xref:System.Windows.Forms.BindingSource>。  
  
5.  F5 キーを押してアプリケーションを実行します。 **DeleteItem** ボタンが無効になっていて、Del キーを押しても項目を削除できないことを確認します。  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a>DataRepeater コントロールに検索機能を追加する  
 この省略可能な手順の値を検索する機能を実装する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 検索文字列が見つかると、このコントロールはその値を含む項目を選択し、スクロールして表示します。  
  
#### <a name="to-add-search-capability"></a>検索機能を追加するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.TextBox>コントロールから、**ツールボックス**を含むフォーム上に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:System.Windows.Forms.TextBox>。  
  
     位置の下に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
2.  [プロパティ] ウィンドウで、 **Name** プロパティを **SearchTextBox**に変更します。  
  
3.  ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**を含むフォーム上に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:System.Windows.Forms.Button>。 位置の下に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
4.  [プロパティ] ウィンドウで、 **Name** プロパティを **SearchButton**に変更します。 **Text** プロパティを **Search**に変更します。  
  
5.  ダブルクリックして、<xref:System.Windows.Forms.Button>を開くには、コード エディターを制御し、次のコードを追加、`SearchButton_Click`イベント ハンドラー</xref:System.Windows.Forms.Button> 。  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  F5 キーを押してアプリケーションを実行します。 **[SearchTextBox]** に顧客 ID を入力し、 **[Search]** ボタンをクリックします。  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a>DataRepeater にマスター/詳細テーブルを追加する  
 この省略可能な手順では、1 秒あたり追加<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>各顧客に関連する注文を表示するコントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
#### <a name="to-add-a-master-and-detail-table"></a>マスター/詳細テーブルを追加するには  
  
1.  1 秒間をドラッグして<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールから、 **Visual Basic power Packs**  タブで、**ツールボックス**フォーム上にします</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
2.  [プロパティ] ウィンドウで、 **Location** プロパティを `465, 25`に設定します。  
  
3.  **Size** プロパティを `315, 600`に設定します。  
  
4.  **[データ ソース]** ウィンドウで、 **[Customers]** テーブル ノードを展開し、 **Orders** テーブルの詳細ノードを選択します。  
  
5.  この **Orders** テーブルのドロップ タイプを、テーブル ノードのドロップダウン リストの **[詳細]** をクリックして [詳細] に変更します。  
  
6.  これをドラッグして**注文**テーブル ノードを&2; 番目の項目テンプレートの領域 (上の領域) に<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
     **OrdersBindingSource** コンポーネントおよび **OrdersTableAdapter** コンポーネントがコンポーネント トレイに追加されます。  
  
7.  F5 キーを押してアプリケーションを実行します。 最初のそれぞれの顧客を選択すると<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>制御の場合は、その顧客は、2 番目に表示されるの注文<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
## <a name="see-also"></a>関連項目  
 [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [方法: DataRepeater コントロールにバインドされたデータの表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [方法: DataRepeater コントロールでコントロールが画面にバインドされていません。](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [方法: DataRepeater コントロールのレイアウトを変更します。](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [方法: DataRepeater コントロールに項目ヘッダーを表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)   
 [方法: DataRepeater コントロールでデータを検索](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)   
 [方法:&2; つの DataRepeater コントロール (Visual Studio) を使用してマスター/詳細フォームを作成](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [方法: DataRepeater コントロールの外観を変更します。](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [方法: 追加と削除 DataRepeater の項目を無効にします。](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)   
 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
