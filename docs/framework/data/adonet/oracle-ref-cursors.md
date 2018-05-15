---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7aae9b2e4b39cf164a93ba82212b5705f583d761
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="086c3-102">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="086c3-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="086c3-103">.NET Framework Data Provider for Oracle には、Oracle がサポートしている**REF CURSOR**データ型。</span><span class="sxs-lookup"><span data-stu-id="086c3-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="086c3-104">データ プロバイダーを使用して Oracle REF CURSOR を操作するときは、次の動作を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="086c3-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="086c3-105">動作の中には、Microsoft OLE DB Provider for Oracle (MSDAORA) の動作と異なるものがあります。</span><span class="sxs-lookup"><span data-stu-id="086c3-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
-   <span data-ttu-id="086c3-106">パフォーマンス上の理由から、Data Provider for Oracle に自動的にはバインドしません**REF CURSOR**データ型を MSDAORA と、明示的に指定する場合を除き、します。</span><span class="sxs-lookup"><span data-stu-id="086c3-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
-   <span data-ttu-id="086c3-107">データ プロバイダーでは、REF CURSOR パラメーターの指定に使用する {resultset} エスケープのような、ODBC エスケープ シーケンスはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="086c3-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
-   <span data-ttu-id="086c3-108">REF Cursor を返すストアド プロシージャを実行するには、内のパラメーターを定義する必要があります、<xref:System.Data.OracleClient.OracleParameterCollection>で、<xref:System.Data.OracleClient.OracleType>の**カーソル**と<xref:System.Data.OracleClient.OracleParameter.Direction%2A>の**出力**です。</span><span class="sxs-lookup"><span data-stu-id="086c3-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="086c3-109">データ プロバイダーでは、REF CURSOR のバインドは出力パラメーターとしてのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="086c3-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="086c3-110">プロバイダーは、入力パラメーターとしての REF CURSOR はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="086c3-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
-   <span data-ttu-id="086c3-111">パラメーター値からの <xref:System.Data.OracleClient.OracleDataReader> の取得はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="086c3-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="086c3-112">値は、コマンドを実行すると <xref:System.DBNull> 型になります。</span><span class="sxs-lookup"><span data-stu-id="086c3-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
-   <span data-ttu-id="086c3-113">唯一**CommandBehavior** REF Cursor で動作する列挙値 (を呼び出すときに、 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) は**CloseConnection**; 他のすべてのユーザーは無視されます。</span><span class="sxs-lookup"><span data-stu-id="086c3-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
-   <span data-ttu-id="086c3-114">内の REF Cursor の順序、 **OracleDataReader**では、パラメーターの順序によって異なります、 **OracleParameterCollection**です。</span><span class="sxs-lookup"><span data-stu-id="086c3-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="086c3-115"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> プロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="086c3-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
-   <span data-ttu-id="086c3-116">PL/SQL**テーブル**データ型はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="086c3-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="086c3-117">ただし、REF CURSOR は、さらに効果的です。</span><span class="sxs-lookup"><span data-stu-id="086c3-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="086c3-118">使用する場合、**テーブル**MSDAORA で OLE DB .NET データ プロバイダーを使用して、データ型します。</span><span class="sxs-lookup"><span data-stu-id="086c3-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="086c3-119">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="086c3-119">In This Section</span></span>  
 [<span data-ttu-id="086c3-120">REF CURSOR の例</span><span class="sxs-lookup"><span data-stu-id="086c3-120">REF CURSOR Examples</span></span>](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 <span data-ttu-id="086c3-121">次の 3 つの例を使って REF CURSOR の使い方について説明します。</span><span class="sxs-lookup"><span data-stu-id="086c3-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="086c3-122">OracleDataReader の REF CURSOR パラメーター</span><span class="sxs-lookup"><span data-stu-id="086c3-122">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="086c3-123">返し、REF CURSOR パラメーターとして値を読み取る、PL/SQL ストアド プロシージャを実行する方法を示します、 **OracleDataReader**です。</span><span class="sxs-lookup"><span data-stu-id="086c3-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="086c3-124">OracleDataReader を使用した複数の REF CURSOR からのデータの取得</span><span class="sxs-lookup"><span data-stu-id="086c3-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="086c3-125">2 つの REF CURSOR パラメーターを返しを使用して値を読み取る PL/SQL ストアド プロシージャを実行する方法を示します、 **OracleDataReader**です。</span><span class="sxs-lookup"><span data-stu-id="086c3-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="086c3-126">1 つまたは複数の REF CURSOR を使用した DataSet の値の設定</span><span class="sxs-lookup"><span data-stu-id="086c3-126">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="086c3-127">2 つの REF CURSOR パラメーターを返し、返された行を <xref:System.Data.DataSet> に入力する、PL/SQL ストアド プロシージャを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="086c3-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="086c3-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="086c3-128">See Also</span></span>  
 [<span data-ttu-id="086c3-129">Oracle および ADO.NET</span><span class="sxs-lookup"><span data-stu-id="086c3-129">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="086c3-130">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="086c3-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
