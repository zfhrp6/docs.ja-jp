---
title: SQL Server の CLR 統合セキュリティ
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 8df8a19850e9cce28b1f09e80908dafb8bfedaf6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361003"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="50732-102">SQL Server の CLR 統合セキュリティ</span><span class="sxs-lookup"><span data-stu-id="50732-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="50732-103">Microsoft SQL Server で新たに導入された機能の 1 つに、.NET Framework の共通言語ランタイム (CLR) コンポーネントの統合があります。</span><span class="sxs-lookup"><span data-stu-id="50732-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="50732-104">CLR の統合により、Microsoft Visual Basic .NET や Microsoft Visual C# を含む任意の .NET Framework 言語を使用して、ストアド プロシージャ、トリガー、ユーザー定義型、ユーザー定義関数、ユーザー定義集計、およびストリーミング テーブル値関数を作成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="50732-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="50732-105">CLR は、コード アクセス セキュリティ (CAS) と呼ばれるマネージ コード用のセキュリティ モデルをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="50732-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="50732-106">このモデルでは、コードのメタデータに指定された証拠に基づいてアセンブリに権限が付与されます。</span><span class="sxs-lookup"><span data-stu-id="50732-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="50732-107">SQL Server のユーザーベースのセキュリティ モデルは、SQL Server により CLR のコード アクセスベースのセキュリティ モデルと統合されます。</span><span class="sxs-lookup"><span data-stu-id="50732-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="50732-108">外部リソース</span><span class="sxs-lookup"><span data-stu-id="50732-108">External Resources</span></span>  
 <span data-ttu-id="50732-109">SQL Server と CLR の統合の詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="50732-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="50732-110">リソース</span><span class="sxs-lookup"><span data-stu-id="50732-110">Resource</span></span>|<span data-ttu-id="50732-111">説明</span><span class="sxs-lookup"><span data-stu-id="50732-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="50732-112">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="50732-112">Code Access Security</span></span>](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)|<span data-ttu-id="50732-113">.NET Framework の CAS について説明します。</span><span class="sxs-lookup"><span data-stu-id="50732-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="50732-114">CLR 統合のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="50732-114">CLR Integration Security</span></span>](http://go.microsoft.com/fwlink/?LinkId=59998)|<span data-ttu-id="50732-115">SQL Server の内部で実行されるマネージ コードのセキュリティ モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="50732-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50732-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="50732-116">See Also</span></span>  
 [<span data-ttu-id="50732-117">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="50732-117">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="50732-118">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="50732-118">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="50732-119">SQL Server の共通言語ランタイム統合</span><span class="sxs-lookup"><span data-stu-id="50732-119">SQL Server Common Language Runtime Integration</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 [<span data-ttu-id="50732-120">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="50732-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
