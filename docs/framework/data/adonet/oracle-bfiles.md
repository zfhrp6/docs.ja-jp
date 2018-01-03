---
title: Oracle BFILE
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 585245464ce3a2ef4b1da6ec2a7e2770af187876
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="oracle-bfiles"></a>Oracle BFILE
.NET Framework Data Provider for Oracle には、<xref:System.Data.OracleClient.OracleBFile> クラスが含まれています。このクラスは、Oracle <xref:System.Data.OracleClient.OracleType.BFile> データ型で使用されます。  
  
 Oracle **BFILE**データ型は、Oracle **LOB**を 4 ギガバイト単位の最大サイズのバイナリ データへの参照を含むデータ型。 Oracle **BFILE**他の Oracle とは異なります**LOB**データ型の代わりに、オペレーティング システムで、サーバー上の物理ファイルにそのデータを格納します。 なお、 **BFILE**データ型は、データへの読み取り専用のアクセスを提供します。  
  
 他の特性、 **BFILE**から区別するためのデータ型、 **LOB**データ型はできることです。  
  
-   非構造化データの保持。  
  
-   サーバー側チャンキングのサポート。  
  
-   参照コピーのセマンティクスの使用。 コピー操作を実行する場合など、 **BFILE**、のみ、 **BFILE**ロケーター (ファイルへの参照は、) をコピーします。 ファイル内のデータはコピーされません。  
  
 **BFILE**サイズが大きい Lob を参照するために使用するデータの種類とそのため、データベースに格納するには実用的ではないです。 複数クライアント、サーバー、および通信のオーバーヘッドを使用する場合、 **BFILE**データ型と比較して、 **LOB**データ型。 アクセスする方が効率的である、 **BFILE**のみ少量のデータを取得する必要がある場合。 オブジェクト全体を取得したい場合は、データベースに常駐する LOB へのアクセスがいっそう効果的です。  
  
 各 NULL **OracleBFile**オブジェクトが、基になる物理ファイルの場所を定義する 2 つのエンティティと関連付けられています。  
  
1.  Oracle DIRECTORY オブジェクト。ファイル システムのディレクトリに対するデータベースのエイリアスです。  
  
2.  基になる物理ファイルのファイル名。このファイルは、DIRECTORY オブジェクトに関連付けられたディレクトリに配置されています。  
  
## <a name="example"></a>例  
 次の c# の例では、作成する方法を示しています、 **BFILE** 、Oracle テーブルにし、それの形式で取得、 **OracleBFile**オブジェクト。 この例では、使用方法を示します、<xref:System.Data.OracleClient.OracleDataReader>オブジェクトおよび**OracleBFile** **シーク**と**読み取り**メソッドです。 このサンプルを使用するためにする必要がありますまずを作成するという名前のディレクトリ"c:\\\bfiles"Oracle サーバーで"MyFile.jpg"という名前のファイルとします。  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =   
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =   
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a>参照  
 [Oracle および ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
