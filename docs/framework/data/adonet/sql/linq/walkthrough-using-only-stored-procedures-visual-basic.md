---
title: "Walkthrough: Using Only Stored Procedures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Walkthrough: Using Only Stored Procedures (Visual Basic)
このチュートリアルでは、ストアド プロシージャのみを使用してデータにアクセスする、基本の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] シナリオ全体を示します。  この方法は、データ ストアへのアクセス方法を制限する目的で、データベース管理者によってよく使用されます。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションでストアド プロシージャを使用して、既定の動作をオーバーライドすることもできます。これは、`Create`、`Update`、および `Delete` の各プロセスで特に役立ちます。  詳細については、「[Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)」を参照してください。  
  
 このチュートリアルでは、Northwind サンプル データベース内のストアド プロシージャにマップされた 2 つのメソッド \(CustOrdersDetail および CustOrderHist\) を使用します。  SqlMetal コマンド ライン ツールを実行して [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ファイルを生成すると、対応付けが発生します。  詳細については、このチュートリアルの「前提条件」を参照してください。  
  
 このチュートリアルは、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]には依存しません。  [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している開発者は、[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]を使用して、ストアド プロシージャの機能を実装することもできます。  「[LINQ to Visual Studio での SQL ツール](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio2.md)」を参照してください。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 このチュートリアルは、Visual Basic 開発設定を使用して記述されています。  
  
## 必須コンポーネント  
 このチュートリアルの前提条件は次のとおりです。  
  
-   このチュートリアルでは、専用フォルダー \("c:\\linqtest3"\) を使用してファイルを保持します。  チュートリアルを開始する前に、このフォルダーを作成してください。  
  
-   Northwind サンプル データベース。  
  
     開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード サイトからダウンロードします。  手順については、「[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)」を参照してください。  データベースをダウンロードしたら、northwnd.mdf ファイルを c:\\linqtest3 フォルダーにコピーします。  
  
-   Northwind データベースから生成された [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] コード ファイル。  
  
     このチュートリアルは、SqlMetal ツールを使用して次のコマンド ラインで作成されています。  
  
     **sqlmetal \/code:"c:\\linqtest3\\northwind.vb" \/language:vb "c:\\linqtest3\\northwnd.mdf" \/sprocs \/functions \/pluralize**  
  
     詳細については、「[SqlMetal.exe \(コード生成ツール\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」を参照してください。  
  
## 概要  
 このチュートリアルは、主に次の 6 つの手順で構成されています。  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] ソリューションを設定します。  
  
-   プロジェクトに System.Data.Linq アセンブリを追加します。  
  
-   プロジェクトにデータベース コード ファイルを追加します。  
  
-   データベースへの接続を作成します。  
  
-   ユーザー インターフェイスを設定します。  
  
-   アプリケーションを実行およびテストします。  
  
## LINQ to SQL ソリューションを作成する  
 最初に、[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] プロジェクトをビルドおよび実行するために必要な参照を含む [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ソリューションを作成します。  
  
#### LINQ to SQL ソリューションを作成するには  
  
1.  [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] の **\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの **\[プロジェクトの種類\]** ペインで、**\[Visual Basic\]** を展開し、**\[Windows\]** をクリックします。  
  
3.  **\[テンプレート\]** ペインの **\[Windows フォーム アプリケーション\]** をクリックします。  
  
4.  **\[名前\]** ボックスに、「SprocOnlyApp」と入力します。  
  
5.  **\[OK\]** をクリックします。  
  
     Windows フォーム デザイナーが開きます。  
  
## LINQ to SQL アセンブリ参照を追加する  
 標準の Windows フォーム アプリケーション テンプレートには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アセンブリは含まれていません。  次の手順に従って、アセンブリを自分で追加する必要があります。  
  
#### System.Data.Linq.dll を追加するには  
  
1.  **ソリューション エクスプローラー**で、**\[すべてのファイルを表示\]** をクリックします。  
  
2.  **ソリューション エクスプローラー**で、**\[参照設定\]** を右クリックし、**\[参照の追加\]** をクリックします。  
  
3.  **\[参照の追加\]** ダイアログ ボックスで、**\[.NET\]** をクリックし、System.Data.Linq アセンブリをクリックします。次に、**\[OK\]** をクリックします。  
  
     アセンブリがプロジェクトに追加されます。  
  
## プロジェクトに Northwind コード ファイルを追加する  
 この手順では、事前に SqlMetal ツールを使用して、Northwind サンプル データベースからコード ファイルを生成していることが前提となります。  詳細については、このチュートリアルの「前提条件」を参照してください。  
  
#### プロジェクトに Northwind コード ファイルを追加するには  
  
1.  \[プロジェクト\] メニューの \[既存のアイテムの追加\] をクリックします。  
  
2.  **\[既存項目の追加\]** ダイアログ ボックスで c:\\linqtest3\\northwind.vb ファイルに移動し、**\[追加\]** をクリックします。  
  
     プロジェクトに northwind.vb ファイルが追加されます。  
  
## データベース接続を作成する  
 この手順では、Northwind サンプル データベースへの接続を定義します。  このチュートリアルでは、パスとして "c:\\linqtest3\\northwnd.mdf" を使用します。  
  
#### データベース接続を作成するには  
  
1.  **ソリューション エクスプローラー**で **\[Form1.vb\]** を右クリックし、**\[コードの表示\]** をクリックします。  
  
     コード エディターに `Class Form1` が表示されます。  
  
2.  `Form1` コード ブロックに次のコードを入力します。  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## ユーザー インターフェイスを設定する  
 この手順では、ユーザーがストアド プロシージャを実行してデータベース内のデータにアクセスできるように、インターフェイスを作成します。  このチュートリアルで作成するアプリケーションでは、ユーザーはアプリケーションに埋め込まれているストアド プロシージャを使用してのみ、データベース内のデータにアクセスできます。  
  
#### ユーザー インターフェイスを設定するには  
  
1.  Windows フォーム デザイナーに戻ります \(**\[Form1.vb \[デザイン\]\]**\)。  
  
2.  **\[表示\]** メニューの **\[ツールボックス\]** をクリックします。  
  
     ツールボックスが表示されます。  
  
    > [!NOTE]
    >  このセクションの残りの手順を実行する間、ツールボックスを開いたままにしておくには、**\[自動的に隠す\]** プッシュピンをクリックします。  
  
3.  ツールボックスから、2 つのボタン、2 つのテキスト ボックス、および 2 つのラベルを **Form1** にドラッグします。  
  
     図のようにコントロールを配置します。  コントロールを簡単に配置できるように、**Form1** のサイズを拡大します。  
  
4.  **\[Label1\]** を右クリックし、**\[プロパティ\]** をクリックします。  
  
5.  **Text** プロパティを **\[Label1\]** から **\[Enter OrderID:\]** に変更します。  
  
6.  **Label2** についても同様に、**Text** プロパティを **\[Label2\]** から **\[Enter CustomerID:\]** に変更します。  
  
7.  同様に、**Button1** の **Text** プロパティを **\[Order Details\]** に変更します。  
  
8.  **Button2** の **Text** プロパティを **\[Order History\]** に変更します。  
  
     すべてのテキストが表示されるように、ボタン コントロールの幅を広げます。  
  
#### ボタン クリックを処理するには  
  
1.  **\[Form1\]** の **\[Order Details\]** をダブルクリックして `Button1` イベント ハンドラーを作成し、コード エディターを開きます。  
  
2.  `Button1` のハンドラーに次のコードを入力します。  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3.  \[Form1\] の **\[Button2\]** をダブルクリックして `Button2` イベント ハンドラーを作成し、コード エディターを開きます。  
  
4.  `Button2` のハンドラーに次のコードを入力します。  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## アプリケーションのテスト  
 次に、アプリケーションをテストします。  データ ストアに対する操作は、2 つのストアド プロシージャで実行できる処理に制限されることに注意してください。  つまり、入力した orderID に含まれている製品を返す処理と、入力した CustomerID の注文製品の履歴を返す処理のみを実行できます。  
  
#### アプリケーションをテストするには  
  
1.  F5 キーを押してデバッグを開始します。  
  
     Form1 が表示されます。  
  
2.  **\[Enter OrderID\]** ボックスに「10249」と入力し、**\[Order Details\]** をクリックします。  
  
     注文 10249 に含まれている製品がメッセージ ボックスに表示されます。  
  
     **\[OK\]** をクリックしてメッセージ ボックスを閉じます。  
  
3.  **\[Enter CustomerID\]** ボックスに「`ALFKI`」と入力し、**\[Order History\]** をクリックします。  
  
     メッセージ ボックスに、顧客 ALFKI の注文履歴が表示されます。  
  
     **\[OK\]** をクリックしてメッセージ ボックスを閉じます。  
  
4.  **\[Enter OrderID\]** ボックスに「`123`」と入力し、**\[Order Details\]** をクリックします。  
  
     メッセージ ボックスに "No results" が表示されます。  
  
     **\[OK\]** をクリックしてメッセージ ボックスを閉じます。  
  
5.  **\[デバッグ\]** メニューの **\[デバッグの停止\]** をクリックします。  
  
     デバッグ セッションが終了します。  
  
6.  操作が終了したら、**\[ファイル\]** メニューの **\[プロジェクトを閉じる\]** をクリックし、メッセージに従ってプロジェクトを保存します。  
  
## 次の手順  
 いくつかの変更を加えることによって、このプロジェクトを強化できます。  たとえば、使用できるストアド プロシージャの一覧をリスト ボックスに表示し、実行するプロシージャをユーザーに選択させることができます。  レポートの出力をテキスト ファイルに送ることもできます。  
  
## 参照  
 [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)   
 [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)