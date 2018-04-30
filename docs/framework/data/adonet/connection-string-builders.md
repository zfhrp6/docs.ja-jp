---
title: 接続文字列ビルダー
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: beec0aba34bc38ba310aa87dadeeaa4b41c82649
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="connection-string-builders"></a><span data-ttu-id="e7163-102">接続文字列ビルダー</span><span class="sxs-lookup"><span data-stu-id="e7163-102">Connection String Builders</span></span>
<span data-ttu-id="e7163-103">[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] の以前のバージョンでは、コンパイル時に文字列の値を連結した接続文字列のチェックが行われなかったために、実行時に不正なキーワードによる <xref:System.ArgumentException> が発生していました。</span><span class="sxs-lookup"><span data-stu-id="e7163-103">In earlier versions of [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="e7163-104">接続文字列のキーワードの構文は [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] のデータ プロバイダーごとに異なるため、有効な接続文字列を手動で作成するのが難しいという問題がありました。</span><span class="sxs-lookup"><span data-stu-id="e7163-104">Each of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="e7163-105">この問題に対処するため、[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 では、各 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] データ プロバイダー用の新しい接続文字列ビルダーが導入されました。</span><span class="sxs-lookup"><span data-stu-id="e7163-105">To address this problem, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 introduced new connection string builders for each [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="e7163-106">各データ プロバイダーは、<xref:System.Data.Common.DbConnectionStringBuilder> から継承した、厳密に型指定された接続文字列ビルダー クラスを提供しています。</span><span class="sxs-lookup"><span data-stu-id="e7163-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="e7163-107">次の表は、各 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] データ プロバイダーおよび対応する接続文字列ビルダー クラスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e7163-107">The following table lists the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="e7163-108">プロバイダー</span><span class="sxs-lookup"><span data-stu-id="e7163-108">Provider</span></span>|<span data-ttu-id="e7163-109">ConnectionStringBuilder クラス</span><span class="sxs-lookup"><span data-stu-id="e7163-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="e7163-110">接続文字列のインジェクション攻撃</span><span class="sxs-lookup"><span data-stu-id="e7163-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="e7163-111">ユーザー入力から文字列を動的に連結することによって接続文字列を構築している場合、接続文字列のインジェクション攻撃を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e7163-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="e7163-112">文字列の検証や悪意のある文字のエスケープを怠ると、機密データなど、サーバー上のリソースへのアクセスを攻撃者に許してしまうことも考えられます。</span><span class="sxs-lookup"><span data-stu-id="e7163-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="e7163-113">たとえば、セミコロンに続けて値を追加するだけでも攻撃が成立します。</span><span class="sxs-lookup"><span data-stu-id="e7163-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="e7163-114">接続文字列は "後勝ち" のアルゴリズムで解析されるため、悪質な入力データによって本来の値が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="e7163-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="e7163-115">接続文字列ビルダー クラスは推測に頼った作業を排除し、構文エラーやセキュリティ上の脆弱性を防ぐことを目的に設計されています。</span><span class="sxs-lookup"><span data-stu-id="e7163-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="e7163-116">このクラスには、各データ プロバイダーによってサポートされた既知のキーと値のペアに対応するプロパティおよびメソッドが存在します。</span><span class="sxs-lookup"><span data-stu-id="e7163-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="e7163-117">それぞれのクラスは、あらかじめ決められた一連のシノニムを管理しており、特定のシノニムを対応する既知のキー名に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="e7163-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="e7163-118">有効なキーと値のペアに対してチェックが実行され、無効なペアが見つかると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e7163-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="e7163-119">また、挿入された値は安全な方法で処理されます。</span><span class="sxs-lookup"><span data-stu-id="e7163-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="e7163-120">次の例を実行すると、<xref:System.Data.SqlClient.SqlConnectionStringBuilder> の設定に対して挿入された余分な値が、`Initial Catalog` によってどのように処理されるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e7163-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
```vb  
Dim builder As New System.Data.SqlClient.SqlConnectionStringBuilder  
builder("Data Source") = "(local)"  
builder("Integrated Security") = True  
builder("Initial Catalog") = "AdventureWorks;NewValue=Bad"  
Console.WriteLine(builder.ConnectionString)  
```  
  
```csharp  
System.Data.SqlClient.SqlConnectionStringBuilder builder =  
  new System.Data.SqlClient.SqlConnectionStringBuilder();  
builder["Data Source"] = "(local)";  
builder["integrated Security"] = true;  
builder["Initial Catalog"] = "AdventureWorks;NewValue=Bad";  
Console.WriteLine(builder.ConnectionString);  
```  
  
 <span data-ttu-id="e7163-121">出力結果を見ると、挿入された値が <xref:System.Data.SqlClient.SqlConnectionStringBuilder> によって適切に処理されていることがわかります。二重引用符内の余分な値は、新しいキーと値のペアとして接続文字列に追加されるのではなくエスケープされています。</span><span class="sxs-lookup"><span data-stu-id="e7163-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="e7163-122">構成ファイルからの接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="e7163-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="e7163-123">接続文字列の特定の要素があらかじめわかっている場合、接続文字列を構成ファイルに格納しておき、それを実行時に取得することによって完全な接続文字列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="e7163-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="e7163-124">たとえば、サーバー名は不明でも、データベースの名前はあらかじめ把握できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e7163-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="e7163-125">または、ユーザーに名前とパスワードだけを実行時に指定してもらい、それ以外の値を接続文字列に挿入できないようにしたい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e7163-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="e7163-126">接続文字列ビルダーには、<xref:System.String> を引数として受け取るオーバーロード コンストラクターがあります。この引数に対して接続文字列を部分的に指定しておき、それ以外の部分をユーザー入力で補完することも可能です。</span><span class="sxs-lookup"><span data-stu-id="e7163-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="e7163-127">部分的な接続文字列は構成ファイルに保存し、実行時に取得できます。</span><span class="sxs-lookup"><span data-stu-id="e7163-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7163-128">構成ファイルへのプログラム アクセスは <xref:System.Configuration> 名前空間によって実現できます。Web アプリケーションの場合は <xref:System.Web.Configuration.WebConfigurationManager> を、Windows アプリケーションの場合は <xref:System.Configuration.ConfigurationManager> を使用します。</span><span class="sxs-lookup"><span data-stu-id="e7163-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="e7163-129">接続文字列と構成ファイルの操作の詳細については、次を参照してください。[接続文字列と構成ファイル](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)です。</span><span class="sxs-lookup"><span data-stu-id="e7163-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="e7163-130">例</span><span class="sxs-lookup"><span data-stu-id="e7163-130">Example</span></span>  
 <span data-ttu-id="e7163-131">この例では、接続文字列の一部を構成ファイルから取得し、<xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> の <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A> プロパティ、<xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> プロパティ、および <xref:System.Data.SqlClient.SqlConnectionStringBuilder> プロパティを設定することによって接続文字列全体を作成します。</span><span class="sxs-lookup"><span data-stu-id="e7163-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="e7163-132">構成ファイルは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="e7163-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="e7163-133">このコードを実行するには、プロジェクトで `System.Configuration.dll` を参照設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7163-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e7163-134">参照</span><span class="sxs-lookup"><span data-stu-id="e7163-134">See Also</span></span>  
 [<span data-ttu-id="e7163-135">接続文字列</span><span class="sxs-lookup"><span data-stu-id="e7163-135">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="e7163-136">プライバシーとデータ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e7163-136">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 [<span data-ttu-id="e7163-137">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="e7163-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
