---
title: "ADO.NET での side-by-side 実行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# ADO.NET での side-by-side 実行
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の side\-by\-side 実行は、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の複数のバージョンがインストールされている 1 台のコンピューター上で、アプリケーションのコンパイル時のバージョンのみを使用して、アプリケーションを実行する機能です。  side\-by\-side 実行の設定の詳細については、「[side\-by\-side 実行](../../../../docs/framework/deployment/side-by-side-execution.md)」を参照してください。  
  
 あるバージョンの [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] を使用してコンパイルされたアプリケーションを、別のバージョンの [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] で実行することもできます。  ただし、インストールされている [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] のバージョンごとにアプリケーションをコンパイルして、各バージョンを別々に実行することをお勧めします。  いずれの場合でも、[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] の各リリース間の変更によって生じるアプリケーションの上位互換性または下位互換性の問題に注意する必要があります。  
  
## 上位互換性と下位互換性  
 上位互換性とは、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の旧バージョンでコンパイルしたアプリケーションが、新しいバージョンの [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] でも実行できることを意味します。  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1 用に書かれた [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] コードは、後のバージョンとの上位互換性があります。  
  
 下位互換性とは、アプリケーションが [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の新しいバージョン用にコンパイルされ、機能を低下させずに、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の以前のバージョンで引き続き実行できることを意味します。  当然のことながら、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の新しいバージョンで導入された機能については、これは該当しません。  
  
## .NET Framework Data Provider for ODBC  
 Version 1.1 以降、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for ODBC \(<xref:System.Data.Odbc>\) は、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の一部として同梱されています。  ODBC データ プロバイダーは、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] バージョン 1.0 の開発者が、Web ダウンロードとして、[データ アクセスおよびストレージ デベロッパー センター](http://go.microsoft.com/fwlink/?linkid=4173)から利用することができます。  ダウンロードされた [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for ODBC の名前空間は **Microsoft.Data.Odbc** です。  
  
 ODBC データ プロバイダーを使用してデータ ソースに接続する、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.0 用に開発したアプリケーションがあり、そのアプリケーションを [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.1 以降で実行する場合は、ODBC データ プロバイダーの名前空間を **System.Data.Odbc** に更新する必要があります。  その後で、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の新しいバージョン用に再コンパイルする必要があります。  
  
 ODBC データ プロバイダーを使用してデータ ソースに接続する [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 2.0 以降用に開発したアプリケーションがあり、そのアプリケーションを [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.0 で実行する場合は、ODBC データ プロバイダーをダウンロードし、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.0 システムにインストールする必要があります。  次に、ODBC データ プロバイダーの名前空間を **Microsoft.Data.Odbc** に変更し、アプリケーションを [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.0 用に再コンパイルする必要があります。  
  
## .NET Framework Data Provider for Oracle  
 Version 1.1 以降、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle \(<xref:System.Data.OracleClient>\) は、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の一部として同梱されています。  データ プロバイダーは、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] バージョン 1.0 の開発者が、Web ダウンロードとして、[データ アクセスおよびストレージ デベロッパー センター](http://go.microsoft.com/fwlink/?linkid=4173)から利用することができます。  
  
 このデータ プロバイダーを使用してデータ ソースに接続する、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 2.0 以降用に開発したアプリケーションがあり、そのアプリケーションを [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.0 で実行する場合は、該当するデータ プロバイダーをダウンロードし、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.0 システムにインストールする必要があります。  
  
## コード アクセス セキュリティ  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.0 の [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] データ プロバイダー \(<xref:System.Data.SqlClient>、<xref:System.Data.OleDb>\) を実行するには、FullTrust 権限が必要です。  権限レベルが FullTrust より低いゾーンで [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.0 の [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] データ プロバイダーを使用しようとすると、<xref:System.Security.SecurityException> がスローされます。  
  
 ただし、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 2.0 以降では、部分的に信頼されたゾーンで [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] データ プロバイダーのすべてを使用できるようになりました。  さらに、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.1 の [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] データ プロバイダーに新しいセキュリティ機能が追加されました。  この機能により、特定のセキュリティ ゾーンで使用できる接続文字列を制限することができます。  特定のセキュリティ ゾーンに対して空白のパスワードの使用を禁止することもできます。  詳細については、「[コード アクセス セキュリティと ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)」を参照してください。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] のインストールごとに個別の Security.config ファイルがあるため、セキュリティ設定については、互換性の問題はありません。  ただし、アプリケーションが、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.1 以降に同梱されている [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] の追加のセキュリティ機能に依存している場合は、アプリケーションを Version 1.0 システムに配布することはできません。  
  
## SqlCommand の実行  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.1 以降では、<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> がデータ ソースでコマンドを実行する方法が変更されました。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.0 では、<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> は、**sp\_executesql** ストアド プロシージャのコンテキストですべてのコマンドを実行します。  その結果、接続の状態に影響を与えるコマンド \(たとえば、SET NOCOUNT ON\) は、現在のコマンドの実行だけに適用されます。  接続が開かれている間に実行される後続のコマンドについては、接続の状態は変更されません。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.1 以降では、<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> は、コマンドにパラメーターが含まれている場合だけ、**sp\_executesql** ストアド プロシージャのコンテキストでコマンドを実行します。これにより、パフォーマンスが向上します。  その結果、接続の状態に影響を与えるコマンドが、非パラメーター化コマンドに含まれている場合、接続が開いている間に実行される後続のすべてのコマンドに対して、接続の状態を変更します。  
  
 たとえば、<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> への呼び出しで次のバッチ コマンドが実行されるとします。  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.1 以降では、NOCOUNT は、接続が開いている間に実行される後続のコマンドに対して ON のままです。  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Version 1.0 では、NOCOUNT は、現在のコマンドの実行に対してだけ ON です。  
  
 アプリケーションが、どちらかのバージョンの [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> の動作に依存している場合は、この変更が上位互換性と下位互換性の両方に影響することがあります。  
  
 アプリケーションを [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の以前のバージョンと新しいバージョンの両方で動作させる場合は、どのバージョンで実行された場合にも動作が同じになるように、コードを記述できます。  変更された接続状態が後続のすべてのコマンドでも有効になるようにする場合は、<xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> を使用してコマンドを実行することをお勧めします。  変更された接続状態が後続のコマンドでは無効になるようにする場合は、接続状態をリセットするコマンドを含めるようにしてください。  次に例を示します。  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## 参照  
 [ADO.NET の概要](../../../../docs/framework/data/adonet/ado-net-overview.md)   
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)