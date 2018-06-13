---
title: '方法 : DBML ファイルおよび外部マッピング ファイルを検証する'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 9bf21353aebd0ae57c51b2ddf3b31b5e7f1ac615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362163"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>方法 : DBML ファイルおよび外部マッピング ファイルを検証する
変更した外部マッピング ファイルや .dbml ファイルは、それぞれのスキーマ定義に対して検証する必要があります。 このトピックでは、検証プロセスを実装する手順を Visual Studio ユーザーを示します。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a>.dbml ファイルまたは XML ファイルを検証するには  
  
1.  Visual Studio で**ファイル** メニューのをポイント**開く**、クリックして**ファイル**です。  
  
2.  **ファイルを開く** ダイアログ ボックスで、.dbml ファイルまたは XML マッピング ファイルを検証する をクリックします。  
  
     このファイルで開きます、 **XML エディター**です。  
  
3.  ウィンドウを右クリックし、をクリックして**プロパティ**です。  
  
4.  **プロパティ** ウィンドウの省略記号ボタンをクリックして、**スキーマ**プロパティです。  
  
     **XML スキーマ** ダイアログ ボックスが表示されます。  
  
5.  目的に適したスキーマ定義を見つけます。  
  
    -   DbmlSchema.xsd は、.dbml ファイルを検証するためのスキーマ定義です。 詳細については、次を参照してください。 [LINQ to SQL でのコード生成](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)です。  
  
    -   LinqToSqlMapping.xsd は、外部 XML マッピング ファイルを検証するためのスキーマ定義です。 詳細については、次を参照してください。[外部マッピング](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)です。  
  
6.  **使用**クリック、ドロップ ダウン ボックスを開き、をクリックして目的のスキーマ定義の行の列**このスキーマを使用して**です。  
  
     これで、スキーマ定義ファイルが DBML ファイルまたは XML マッピング ファイルに関連付けられます。  
  
     他のスキーマ定義は選択しないようにしてください。  
  
7.  **ビュー**  メニューのをクリックして**エラー一覧**です。  
  
     エラー、警告、またはメッセージが生成されていないか確認します。 生成されていなければ、XML ファイルはスキーマ定義に対して有効です。  
  
## <a name="alternate-method-for-supplying-schema-definition"></a>スキーマ定義を指定する別の方法  
 何らかの理由により適切な .xsd ファイルが表示されない場合に、 **XML スキーマ**ダイアログ ボックスで、ヘルプ トピックから .xsd ファイルをダウンロードすることができます。 次の手順では、Visual Studio XML エディターで必要な Unicode 形式でダウンロードしたファイルを保存できます。  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>スキーマ定義ファイルをヘルプ トピックからコピーするには  
  
1.  このトピックで既に説明したように、スキーマ定義が含まれているヘルプ トピックを表示します。  
  
    -   .Dbml ファイルを参照してください。 [LINQ to SQL でのコード生成](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)です。  
  
    -   外部マッピング ファイルを参照してください。[外部マッピング](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)です。  
  
2.  をクリックして**コードのコピー**コード ファイルをクリップボードにコピーします。  
  
3.  メモ帳を起動して、新しいファイルを作成します。  
  
4.  クリップボードからメモ帳のファイルにコードを貼り付けます。  
  
5.  メモ帳**ファイル** メニューのをクリックして**名前を付けて保存**です。  
  
6.  **エンコード**ボックスで、 **Unicode**です。  
  
    > [!IMPORTANT]
    >  これを選択することで、テキスト ファイルの先頭に Unicode-16 のバイト順マーカー (`FFFE`) が追加されます。  
  
7.  **ファイル名**ボックスで、ファイル名の拡張子が .xsd で作成します。  
  
## <a name="see-also"></a>関連項目  
 [参照](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
