---
title: CLR ユーザー定義型
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: 344245ea7c67d7b5363c17bb42e2606ca11142bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357583"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="0f347-102">CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="0f347-102">CLR User-Defined Types</span></span>
<span data-ttu-id="0f347-103">Microsoft SQL Server では、Microsoft .NET Framework 共通言語ランタイム (CLR) を使用して実装されるユーザー定義型 (UDT) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0f347-103">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="0f347-104">CLR は SQL Server に統合されており、この機構を利用すると、データベースの型システムを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="0f347-104">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="0f347-105">UDT を利用すれば、SQL Server データ型システムのユーザー拡張が可能であり、複雑な構造化型を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="0f347-105">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="0f347-106">UDT は、アプリケーション アーキテクチャの観点から見て 2 つの重要な利点を備えています。</span><span class="sxs-lookup"><span data-stu-id="0f347-106">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
-   <span data-ttu-id="0f347-107">内部状態と外部動作の間の (クライアントとサーバーの両方での) 強力なカプセル化。</span><span class="sxs-lookup"><span data-stu-id="0f347-107">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
-   <span data-ttu-id="0f347-108">他の関連するサーバー機能との緊密な統合。</span><span class="sxs-lookup"><span data-stu-id="0f347-108">Deep integration with other related server features.</span></span> <span data-ttu-id="0f347-109">独自の UDT を定義すると、列定義、変数、パラメーター、関数の結果、カーソル、トリガー、およびレプリケーションなど、SQL Server のシステム型を利用できるすべてのコンテキストでその UDT を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0f347-109">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="0f347-110">詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f347-110">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="0f347-111">**SQL Server オンライン ブック**</span><span class="sxs-lookup"><span data-stu-id="0f347-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="0f347-112">CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="0f347-112">CLR User-Defined Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="see-also"></a><span data-ttu-id="0f347-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f347-113">See Also</span></span>  
 [<span data-ttu-id="0f347-114">マネージ コードでの SQL Server 2005 のオブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="0f347-114">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="0f347-115">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="0f347-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
