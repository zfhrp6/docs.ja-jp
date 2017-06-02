---
title: "Walkthrough: Manipulating Data (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Walkthrough: Manipulating Data (Visual Basic)
このチュートリアルでは、データベースに対してデータの追加、変更、および削除を行う、基本の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] シナリオ全体を示します。  顧客の追加、顧客名の変更、および注文の削除を行うため、サンプルの Northwind データベースのコピーを使用します。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 このチュートリアルは、Visual Basic 開発設定を使用して記述されています。  
  
## 必須コンポーネント  
 このチュートリアルの前提条件は次のとおりです。  
  
-   このチュートリアルでは、専用フォルダー \("c:\\linqtest2"\) を使用してファイルを保持します。  チュートリアルを開始する前に、このフォルダーを作成してください。  
  
-   Northwind サンプル データベース。  
  
     開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード サイトからダウンロードします。  手順については、「[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)」を参照してください。  データベースをダウンロードしたら、northwnd.mdf ファイルを c:\\linqtest2 フォルダーにコピーします。  
  
-   Northwind データベースから生成された Visual Basic コード ファイル。  
  
     このファイルを生成するには、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]または SQLMetal ツールを使用します。  このチュートリアルは、SQLMetal ツールを使用して次のコマンド ラインで作成されています。  
  
     **sqlmetal \/code:"c:\\linqtest2\\northwind.vb" \/language:vb "C:\\linqtest2\\northwnd.mdf" \/pluralize**  
  
     詳細については、「[SqlMetal.exe \(コード生成ツール\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」を参照してください。  
  
## 概要  
 このチュートリアルは、主に次の 6 つの手順で構成されています。  
  
-   [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] で [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ソリューションを作成します。  
  
-   プロジェクトにデータベース コード ファイルを追加します。  
  
-   新しい顧客オブジェクトを作成します。  
  
-   顧客の連絡先名を変更します。  
  
-   注文を削除します。  
  
-   これらの変更を Northwind データベースに送信します。  
  
## LINQ to SQL ソリューションを作成する  
 最初に、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロジェクトをビルドおよび実行するために必要な参照を含む [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] ソリューションを作成します。  
  
#### LINQ to SQL ソリューションを作成するには  
  
1.  [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] の **\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの **\[プロジェクトの種類\]** ペインで、**\[Visual Basic\]** をクリックします。  
  
3.  **\[テンプレート\]** ペインの **\[コンソール アプリケーション\]** をクリックします。  
  
4.  **\[プロジェクト名\]** ボックスに「LinqDataManipulationApp」と入力します。  
  
5.  **\[OK\]** をクリックします。  
  
## LINQ の参照とディレクティブを追加する  
 このチュートリアルで使用するアセンブリは、既定ではプロジェクトにインストールされていない場合があります。  `System.Data.Linq` がプロジェクトの参照 \(**ソリューション エクスプローラー**で **\[すべてのファイルを表示\]** をクリックし、**\[参照設定\]** ノードを展開\) に表示されていない場合は、以下の手順に従って追加します。  
  
#### System.Data.Linq を追加するには  
  
1.  **ソリューション エクスプローラー**で、**\[参照設定\]** を右クリックし、**\[参照の追加\]** をクリックします。  
  
2.  **\[参照の追加\]** ダイアログ ボックスで、**\[.NET\]** をクリックし、System.Data.Linq アセンブリをクリックします。次に、**\[OK\]** をクリックします。  
  
     アセンブリがプロジェクトに追加されます。  
  
3.  コード エディターで、**Module1** の上に次のディレクティブを追加します。  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## プロジェクトに Northwind コード ファイルを追加する  
 これらの手順では、SQLMetal ツールを使用して Northwind サンプル データベースからコード ファイルを生成していることが前提です。  詳細については、このチュートリアルの「前提条件」を参照してください。  
  
#### プロジェクトに Northwind コード ファイルを追加するには  
  
1.  \[プロジェクト\] メニューの \[既存のアイテムの追加\] をクリックします。  
  
2.  **\[既存項目の追加\]** ダイアログ ボックスで c:\\linqtest2\\northwind.vb に移動し、**\[追加\]** をクリックします。  
  
     プロジェクトに northwind.vb ファイルが追加されます。  
  
## データベース接続の設定  
 最初に、データベースへの接続をテストします。  データベースの名前 Northwnd に i の文字が欠けていることに注意してください。  次の手順でエラーが生成された後で、northwind.vb ファイルを調べて、Northwind 部分クラスのスペルを確認します。  
  
#### データベース接続を設定してテストするには  
  
1.  `Sub Main` に次のコードを入力するか、貼り付けます。  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2.  この時点でアプリケーションをテストするには、F5 キーを押します。  
  
     **コンソール** ウィンドウが開きます。  
  
     **コンソール** ウィンドウで Enter キーを押すか、[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **\[デバッグ\]** メニューの **\[デバッグの停止\]** をクリックして、アプリケーションを閉じます。  
  
## 新しいエンティティの作成  
 新しいエンティティを作成する手順は簡単です。  `New` キーワードを使用してオブジェクト \(`Customer` など\) を作成できます。  
  
 以降のセクションでは、ローカル キャッシュのみに変更を加えます。  このチュートリアルの終盤で <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すまで、変更内容はデータベースに送信されません。  
  
#### 新しい Customer エンティティ オブジェクトを追加するには  
  
1.  次のコードを `Sub Main` 内の `Console.ReadLine` の前に追加することで、新しい `Customer` を作成します。  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2.  F5 キーを押してソリューションをデバッグします。  
  
     結果は、以下のようにコンソール ウィンドウに表示されます。  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     新しい行は結果に表示されません。  新しいデータは、まだデータベースに送信されていません。  
  
3.  **コンソール** ウィンドウで Enter キーを押して、デバッグを停止します。  
  
## エンティティの更新  
 以降の手順では、`Customer` オブジェクトを取得し、そのプロパティの 1 つを変更します。  
  
#### 顧客の名前を変更するには  
  
-   `Console.ReadLine()` の前に次のコードを追加します。  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## エンティティの削除  
 同じ顧客オブジェクトを使用して、最初の注文を削除できます。  
  
 行間のリレーションシップを切断し、データベースから行を削除する方法を次のコードに示します。  
  
#### 行を削除するには  
  
-   `Console.ReadLine()` の直前に次のコードを追加します。  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## 変更内容のデータベースへの送信  
 最後の手順は、オブジェクトの作成、更新、および削除を実際にデータベースに送信するために必要です。  この手順を行わないと、変更はローカルのみに留まり、クエリの結果には反映されません。  
  
#### データベースに変更内容を送信するには  
  
1.  `Console.ReadLine` の直前に次のコードを挿入します。  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2.  変更内容の送信前と送信後の変化を示すために、次のコードを \(`SubmitChanges` の後に\) 挿入します。  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3.  F5 キーを押してソリューションをデバッグします。  
  
     次のようにコンソール ウィンドウが表示されます。  
  
    ```  
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4.  **コンソール** ウィンドウで Enter キーを押して、デバッグを停止します。  
  
> [!NOTE]
>  変更内容を送信して新しい顧客を追加した後で、このソリューションを再度実行することはできません。同じ顧客を再度追加できないためです。  ソリューションを再度実行するには、追加する顧客 ID の値を変更します。  
  
## 参照  
 [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)