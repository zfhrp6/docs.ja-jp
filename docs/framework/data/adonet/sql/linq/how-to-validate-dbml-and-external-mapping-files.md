---
title: "How to: Validate DBML and External Mapping Files | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# How to: Validate DBML and External Mapping Files
変更した外部マッピング ファイルや .dbml ファイルは、それぞれのスキーマ定義に対して検証する必要があります。  このトピックでは、[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] ユーザーを対象に、検証プロセスを実装する手順を示します。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### .dbml ファイルまたは XML ファイルを検証するには  
  
1.  Visual Studio で、**\[ファイル\]** メニューの **\[開く\]** をポイントし、**\[ファイル\]** をクリックします。  
  
2.  **\[ファイルを開く\]** ダイアログ ボックスで、検証する .dbml ファイルまたは XML マッピング ファイルをクリックします。  
  
     **XML エディター**でファイルが開きます。  
  
3.  ウィンドウを右クリックし、**\[プロパティ\]** をクリックします。  
  
4.  **\[プロパティ\]** ウィンドウで、**\[Schemas\]** プロパティの横にある \[...\] ボタンをクリックします。  
  
     **\[XML スキーマ\]** ダイアログ ボックスが表示されます。  
  
5.  目的に適したスキーマ定義を見つけます。  
  
    -   DbmlSchema.xsd は、.dbml ファイルを検証するためのスキーマ定義です。  詳細については、「[Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)」を参照してください。  
  
    -   LinqToSqlMapping.xsd は、外部 XML マッピング ファイルを検証するためのスキーマ定義です。  詳細については、「[External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)」を参照してください。  
  
6.  目的のスキーマ定義の行の **\[使用\]** 列をクリックしてドロップダウン ボックスを表示し、**\[このスキーマを使用する\]** をクリックします。  
  
     これで、スキーマ定義ファイルが DBML ファイルまたは XML マッピング ファイルに関連付けられます。  
  
     他のスキーマ定義は選択しないようにしてください。  
  
7.  **\[表示\]** メニューの **\[エラー一覧\]** をクリックします。  
  
     エラー、警告、またはメッセージが生成されていないか確認します。  生成されていなければ、XML ファイルはスキーマ定義に対して有効です。  
  
## スキーマ定義を指定する別の方法  
 なんらかの理由で **\[XML スキーマ\]** ダイアログ ボックスに適切な .xsd ファイルが表示されない場合は、ヘルプ トピックから .xsd ファイルをダウンロードできます。  次の手順を使用すると、ダウンロードしたファイルを、[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] の XML エディターに対応する Unicode 形式で保存できます。  
  
#### スキーマ定義ファイルをヘルプ トピックからコピーするには  
  
1.  このトピックで既に説明したように、スキーマ定義が含まれているヘルプ トピックを表示します。  
  
    -   .dbml ファイルについては、「[Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)」を参照してください。  
  
    -   外部マッピング ファイルについては、「[External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)」を参照してください。  
  
2.  **\[コードのコピー\]** をクリックして、コード ファイルをクリップボードにコピーします。  
  
3.  メモ帳を起動して、新しいファイルを作成します。  
  
4.  クリップボードからメモ帳のファイルにコードを貼り付けます。  
  
5.  メモ帳で、**\[ファイル\]** メニューの **\[名前を付けて保存\]** をクリックします。  
  
6.  **\[文字コード\]** ボックスの一覧の **\[Unicode\]** をクリックします。  
  
    > [!IMPORTANT]
    >  これを選択することで、テキスト ファイルの先頭に Unicode\-16 のバイト順マーカー \(`FFFE`\) が追加されます。  
  
7.  **\[ファイル名\]** ボックスに、ファイル名と拡張子 .xsd を入力します。  
  
## 参照  
 [Reference](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)