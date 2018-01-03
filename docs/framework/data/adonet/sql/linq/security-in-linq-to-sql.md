---
title: "LINQ to SQL におけるセキュリティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3b3f23be3be6d0c50f015be95b10938178f198bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="security-in-linq-to-sql"></a><span data-ttu-id="61865-102">LINQ to SQL におけるセキュリティ</span><span class="sxs-lookup"><span data-stu-id="61865-102">Security in LINQ to SQL</span></span>
<span data-ttu-id="61865-103">データベースに接続するときは、常にセキュリティのリスクがあります。</span><span class="sxs-lookup"><span data-stu-id="61865-103">Security risks are always present when you connect to a database.</span></span> <span data-ttu-id="61865-104">LINQ to SQL には SQL Server のデータを操作する新しい方法が含まれていますが、セキュリティ メカニズムは追加されていません。</span><span class="sxs-lookup"><span data-stu-id="61865-104">Although LINQ to SQL may include some new ways to work with data in SQL Server, it does not provide any additional security mechanisms.</span></span>  
  
## <a name="access-control-and-authentication"></a><span data-ttu-id="61865-105">アクセス制御と認証</span><span class="sxs-lookup"><span data-stu-id="61865-105">Access Control and Authentication</span></span>  
 <span data-ttu-id="61865-106">LINQ to SQL には独自のユーザー モデルや認証メカニズムがありません。</span><span class="sxs-lookup"><span data-stu-id="61865-106">LINQ to SQL does not have its own user model or authentication mechanisms.</span></span> <span data-ttu-id="61865-107">オブジェクト モデルにマッピングされるデータベース、データベースのテーブル、ビュー、ストアド プロシージャなどへのアクセス制御には SQL Server のセキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="61865-107">Use SQL Server Security to control access to the database, database tables, views, and stored procedures that are mapped to your object model.</span></span> <span data-ttu-id="61865-108">ユーザーには必要最小限のアクセス権を与え、ユーザー認証には強力なパスワードを要求してください。</span><span class="sxs-lookup"><span data-stu-id="61865-108">Grant the minimally required access to users and require strong passwords for user authentication.</span></span>  
  
## <a name="mapping-and-schema-information"></a><span data-ttu-id="61865-109">マッピングとスキーマ情報</span><span class="sxs-lookup"><span data-stu-id="61865-109">Mapping and Schema Information</span></span>  
 <span data-ttu-id="61865-110">オブジェクト モデルまたは外部マッピング ファイルにある、SQL-CLR 型マッピングとデータベース スキーマ情報は、ファイル システムでこれらのファイルに対してアクセス権を持つ全ユーザーに公開されます。</span><span class="sxs-lookup"><span data-stu-id="61865-110">SQL-CLR type mapping and database schema information in your object model or external mapping file is available for all with access to those files in the file system.</span></span> <span data-ttu-id="61865-111">オブジェクト モデルや外部マッピング ファイルにアクセスできるユーザーはすべてスキーマ情報を使用できると想定してください。スキーマ情報へのアクセスを制限するには、ファイルのセキュリティ メカニズムを使用してソース ファイルとマッピング ファイルのセキュリティを確保します。</span><span class="sxs-lookup"><span data-stu-id="61865-111">Assume that schema information will be available to all who can access the object model or external mapping file.To prevent more widespread access to schema information, use file security mechanisms to secure source files and mapping files.</span></span>  
  
## <a name="connection-strings"></a><span data-ttu-id="61865-112">接続文字列</span><span class="sxs-lookup"><span data-stu-id="61865-112">Connection Strings</span></span>  
 <span data-ttu-id="61865-113">接続文字列にパスワードを使用することは、できるだけ避けてください。</span><span class="sxs-lookup"><span data-stu-id="61865-113">Using passwords in connection strings should be avoided whenever possible.</span></span> <span data-ttu-id="61865-114">接続文字列自体がセキュリティのリスクであるうえに、接続文字列はオブジェクト リレーショナル デザイナーまたは SQLMetal コマンド ライン ツールの使用時にオブジェクト モデルや外部マッピング ファイルにクリア テキストで追加できます。</span><span class="sxs-lookup"><span data-stu-id="61865-114">Not only is a connection string a security risk in its own right, but the connection string may also be added in clear text to the object model or external mapping file when using the Object Relational Designer or SQLMetal command-line tool.</span></span> <span data-ttu-id="61865-115">ファイル システムでオブジェクト モデルまたは外部マッピング ファイルに対してアクセス権があれば、どのユーザーでも接続パスワードを見ることができます (パスワードが接続文字列に含まれている場合)。</span><span class="sxs-lookup"><span data-stu-id="61865-115">Anyone with access to the object model or external mapping file via the file system could see the connection password (if it is included in the connection string).</span></span>  
  
 <span data-ttu-id="61865-116">このようなリスクを最小限に抑えるには、統合セキュリティを使用して [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] との信頼関係接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="61865-116">To minimize such risks, use integrated security to make a trusted connection with [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="61865-117">この方法を使用すると、接続文字列にパスワードを含める必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="61865-117">By using this approach, you do not have to store a password in the connection string.</span></span> <span data-ttu-id="61865-118">詳細については、次を参照してください。 [SQL Server のセキュリティ](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md)です。</span><span class="sxs-lookup"><span data-stu-id="61865-118">For more information, see [SQL Server Security](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).</span></span>  
  
 <span data-ttu-id="61865-119">統合セキュリティがない場合は、接続文字列にクリア テキストのパスワードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="61865-119">In the absence of integrated security, a clear-text password will be needed in the connection string.</span></span> <span data-ttu-id="61865-120">以下は、接続文字列のセキュリティ保護に最も有効な手段です。</span><span class="sxs-lookup"><span data-stu-id="61865-120">The best way to help secure your connection string, in increasing order of risk, is as follows:</span></span>  
  
-   <span data-ttu-id="61865-121">統合セキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="61865-121">Use integrated security.</span></span>  
  
-   <span data-ttu-id="61865-122">接続文字列をパスワードで保護し、接続文字列の配布を最小限にします。</span><span class="sxs-lookup"><span data-stu-id="61865-122">Secure connection strings with passwords and minimize passing around connection strings.</span></span>  
  
-   <span data-ttu-id="61865-123">接続文字列の代わりに、表示時間に制限のある <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="61865-123">Use a <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> class instead of a connection string since it limits the duration of exposure.</span></span> <span data-ttu-id="61865-124">LINQ to SQL の <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> クラスは <xref:System.Data.SqlClient.SqlConnection> を使用してインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="61865-124">The LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> class can be instantiated using a <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
-   <span data-ttu-id="61865-125">すべての接続文字列の期限と接触点を最小限にします。</span><span class="sxs-lookup"><span data-stu-id="61865-125">Minimize lifetimes and touch points for all connection strings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61865-126">参照</span><span class="sxs-lookup"><span data-stu-id="61865-126">See Also</span></span>  
 [<span data-ttu-id="61865-127">背景情報</span><span class="sxs-lookup"><span data-stu-id="61865-127">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="61865-128">よく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="61865-128">Frequently Asked Questions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
