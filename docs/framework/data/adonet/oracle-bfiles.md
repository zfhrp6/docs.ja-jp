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
ms.openlocfilehash: f48bd85559d55d9a1190310bcf13cd4a68625011
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-bfiles"></a><span data-ttu-id="2aaeb-102">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="2aaeb-102">Oracle BFILEs</span></span>
<span data-ttu-id="2aaeb-103">.NET Framework Data Provider for Oracle には、<xref:System.Data.OracleClient.OracleBFile> クラスが含まれています。このクラスは、Oracle <xref:System.Data.OracleClient.OracleType.BFile> データ型で使用されます。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="2aaeb-104">Oracle **BFILE**データ型は、Oracle **LOB**を 4 ギガバイト単位の最大サイズのバイナリ データへの参照を含むデータ型。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="2aaeb-105">Oracle **BFILE**他の Oracle とは異なります**LOB**データ型の代わりに、オペレーティング システムで、サーバー上の物理ファイルにそのデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="2aaeb-106">なお、 **BFILE**データ型は、データへの読み取り専用のアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="2aaeb-107">他の特性、 **BFILE**から区別するためのデータ型、 **LOB**データ型はできることです。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
-   <span data-ttu-id="2aaeb-108">非構造化データの保持。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-108">Contains unstructured data.</span></span>  
  
-   <span data-ttu-id="2aaeb-109">サーバー側チャンキングのサポート。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-109">Supports server-side chunking.</span></span>  
  
-   <span data-ttu-id="2aaeb-110">参照コピーのセマンティクスの使用。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-110">Uses reference copy semantics.</span></span> <span data-ttu-id="2aaeb-111">コピー操作を実行する場合など、 **BFILE**、のみ、 **BFILE**ロケーター (ファイルへの参照は、) をコピーします。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="2aaeb-112">ファイル内のデータはコピーされません。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="2aaeb-113">**BFILE**サイズが大きい Lob を参照するために使用するデータの種類とそのため、データベースに格納するには実用的ではないです。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="2aaeb-114">複数クライアント、サーバー、および通信のオーバーヘッドを使用する場合、 **BFILE**データ型と比較して、 **LOB**データ型。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="2aaeb-115">アクセスする方が効率的である、 **BFILE**のみ少量のデータを取得する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="2aaeb-116">オブジェクト全体を取得したい場合は、データベースに常駐する LOB へのアクセスがいっそう効果的です。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="2aaeb-117">各 NULL **OracleBFile**オブジェクトが、基になる物理ファイルの場所を定義する 2 つのエンティティと関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1.  <span data-ttu-id="2aaeb-118">Oracle DIRECTORY オブジェクト。ファイル システムのディレクトリに対するデータベースのエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2.  <span data-ttu-id="2aaeb-119">基になる物理ファイルのファイル名。このファイルは、DIRECTORY オブジェクトに関連付けられたディレクトリに配置されています。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2aaeb-120">例</span><span class="sxs-lookup"><span data-stu-id="2aaeb-120">Example</span></span>  
 <span data-ttu-id="2aaeb-121">次の c# の例では、作成する方法を示しています、 **BFILE** 、Oracle テーブルにし、それの形式で取得、 **OracleBFile**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="2aaeb-122">この例では、使用方法を示します、<xref:System.Data.OracleClient.OracleDataReader>オブジェクトおよび**OracleBFile** **シーク**と**読み取り**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="2aaeb-123">このサンプルを使用するためにする必要がありますまずを作成するという名前のディレクトリ"c:\\\bfiles"Oracle サーバーで"MyFile.jpg"という名前のファイルとします。</span><span class="sxs-lookup"><span data-stu-id="2aaeb-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2aaeb-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="2aaeb-124">See Also</span></span>  
 [<span data-ttu-id="2aaeb-125">Oracle および ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2aaeb-125">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="2aaeb-126">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="2aaeb-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
