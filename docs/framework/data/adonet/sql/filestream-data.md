---
title: "FILESTREAM データ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2fde543187d1904da93be255878d6c7a99de6bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="filestream-data"></a>FILESTREAM データ
FILESTREAM ストレージ属性は、varbinary(max) 列に格納されるバイナリ (BLOB) データに対応しています。 FILESTREAM の導入前は、バイナリ データの格納するために特別な処理が必要でした。 テキスト ドキュメント、イメージ、ビデオなどの非構造化データはデータベース外に保存されることが多く、そのために管理が困難でした。  
  
> [!NOTE]
>  SqlClient を使用して FILESTREAM データを操作するには、.NET Framework 3.5 SP1 以降をインストールする必要があります。  
  
 varbinary(max) 列に FILESTREAM 属性を指定すると、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] では、データがデータベース ファイルではなくローカルの NTFS ファイル システムに保存されます。 データは個別に保存されますが、データベースに保存されている varbinary(max) データの操作のためにサポートされているのと同じ [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] ステートメントを使用できます。  
  
## <a name="sqlclient-support-for-filestream"></a>FILESTREAM の SqlClient サポート  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] (<xref:System.Data.SqlClient>) は、<xref:System.Data.SqlTypes.SqlFileStream> 名前空間で定義された <xref:System.Data.SqlTypes> クラスを使用して、FILESTREAM データの読み取りと書き込みをサポートします。 `SqlFileStream` は <xref:System.IO.Stream> クラスを継承します。このクラスは、データのストリームへの読み込みと書き込みを行うためのメソッドを提供します。 ストリームからデータを読み取ると、データはストリームからバイトの配列などのデータ構造に転送されます。 書き込みを行うと、データはデータ構造からストリームに転送されます。  
  
### <a name="creating-the-includessnoversionincludesssnoversion-mdmd-table"></a>[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] テーブルの作成  
 次の [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] ステートメントでは、従業員の名前の付いたテーブルを作成し、データ行を挿入します。 FILESTREAM ストレージを有効にすると、このテーブルを次のようなコード例と共に使用できます。 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] オンライン ブックの関連トピックへのリンクは、このトピックの最後にあります。  
  
```  
CREATE TABLE employees  
(  
  EmployeeId INT  NOT NULL  PRIMARY KEY,  
  Photo VARBINARY(MAX) FILESTREAM  NULL,  
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL  
  UNIQUE DEFAULT NEWID()  
)  
GO  
Insert into employees  
Values(1, 0x00, default)  
GO  
```  
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>例: FILESTREAM データの読み取り、上書き、および挿入  
 次のサンプルでは、FILESTREAM からデータを読み取る方法を示します。 コードはファイルへの論理パスを取得し、`FileAccess` を `Read` に、`FileOptions` を `SequentialScan` に設定します。 次に、コードは SqlFileStream からバイトをバッファーに読み取ります。 バイトはコンソール ウィンドウに書き込まれます。  
  
 また、このサンプルでは、すべての既存のデータを上書きする FILESTREAM にデータを書き込む方法も示します。 コードはファイルへの論理パスを取得し、`SqlFileStream` を作成し、`FileAccess` を `Write` に、`FileOptions` を `SequentialScan` に設定します。 1 バイトが `SqlFileStream` に書き込まれ、ファイルのデータは置換されます。  
  
 このサンプルでは、Seek メソッドを使用してファイルの末尾にデータを追加することによって、データを FILESTREAM に書き込む方法も示します。 コードはファイルへの論理パスを取得し、`SqlFileStream` を作成し、`FileAccess` を `ReadWrite` に、`FileOptions` を `SequentialScan` に設定します。 コードは Seek メソッドを使用してファイルの末尾をシークし、1 バイトを既存のファイルに追加します。  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Data;  
using System.IO;  
  
namespace FileStreamTest  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");  
            ReadFilestream(builder);  
            OverwriteFilestream(builder);  
            InsertFilestream(builder);  
  
            Console.WriteLine("Done");  
        }  
  
        private static void ReadFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for the file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Read the contents as bytes and write them to the console  
                            for (long index = 0; index < fileStream.Length; index++)  
                            {  
                                Console.WriteLine(fileStream.ReadByte());  
                            }  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void OverwriteFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file   
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Write a single byte to the file. This will  
                            // replace any data in the file.  
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void InsertFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Seek to the end of the file  
                            fileStream.Seek(0, SeekOrigin.End);  
  
                            // Append a single byte   
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
  
        }  
    }  
} using (SqlConnection connection = new SqlConnection(  
    connStringBuilder.ToString()))  
{  
    connection.Open();  
  
    SqlCommand command = new SqlCommand("", connection);  
    command.CommandText = "select Top(1) Photo.PathName(), "  
    + "GET_FILESTREAM_TRANSACTION_CONTEXT () from employees";  
  
    SqlTransaction tran = connection.BeginTransaction(  
        System.Data.IsolationLevel.ReadCommitted);  
    command.Transaction = tran;  
  
    using (SqlDataReader reader = command.ExecuteReader())  
    {  
        while (reader.Read())  
        {  
            // Get the pointer for file  
            string path = reader.GetString(0);  
            byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
            FileStream fileStream = new SqlFileStream(path,  
                (byte[])reader.GetValue(1),  
                FileAccess.ReadWrite,  
                FileOptions.SequentialScan, 0);  
  
            // Seek to the end of the file  
            fs.Seek(0, SeekOrigin.End);  
  
            // Append a single byte   
            fileStream.WriteByte(0x01);  
            fileStream.Close();  
        }  
    }  
    tran.Commit();  
}  
```  
  
 別のサンプルでは、次を参照してください。[保存し、ファイル ストリーム列にバイナリ データをフェッチする方法](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str)です。  
  
## <a name="resources-in-includessnoversionincludesssnoversion-mdmd-books-online"></a>[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] オンライン ブックの関連トピック  
 FILESTREAM の詳細なドキュメントは、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] オンライン ブックの次のセクションにあります。  
  
|トピック|説明|  
|-----------|-----------------|  
|[設計と実装の FILESTREAM ストレージ](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)|FILESTREAM ドキュメントと関連項目へのリンクを示します。|  
|[FILESTREAM の概要](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)|FILESTREAM ストレージを使用するタイミング、および SQL Server データベース エンジンと NTFS ファイル システムを統合する方法について説明します。|  
|[FILESTREAM ストレージの概要](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)|FILESTREAM を SQL Server のインスタンス上で有効にする方法、データベースと FILESTREAM データを格納するテーブルの作成方法、および FILESTREAM データを含んでいる行の操作方法について説明します。|  
|[クライアント アプリケーションで FILESTREAM ストレージを使用します。](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)|FILESTREAM データを操作するための Win32 API 関数について説明します。|  
|[FILESTREAM およびその他の SQL Server の機能](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)|FILESTREAM データを SQL Server の他の機能と共に使用する際の注意事項、ガイドライン、および制限事項について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [SQL Server データ型と ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [ADO.NET でのデータの取得および変更](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [コード アクセス セキュリティと ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [SQL Server のバイナリ データと大きな値のデータ](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
