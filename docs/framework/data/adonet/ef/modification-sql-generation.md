---
title: 変更 SQL 生成
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 1d24775a7a50da1008a5097e1a2caf4e72c946e2
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071953"
---
# <a name="modification-sql-generation"></a><span data-ttu-id="542f5-102">変更 SQL 生成</span><span class="sxs-lookup"><span data-stu-id="542f5-102">Modification SQL Generation</span></span>
<span data-ttu-id="542f5-103">ここでは、SQL:1999 準拠のデータベース プロバイダーのための変更 SQL 生成モジュールを開発する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="542f5-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="542f5-104">このモジュールは、変更コマンド ツリーを適切な SQL INSERT ステートメント、UPDATE ステートメント、または DELETE ステートメントに変換します。</span><span class="sxs-lookup"><span data-stu-id="542f5-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>  
  
 <span data-ttu-id="542f5-105">SQL 生成の select ステートメントの詳細については、次を参照してください。 [SQL 生成](../../../../../docs/framework/data/adonet/ef/sql-generation.md)です。</span><span class="sxs-lookup"><span data-stu-id="542f5-105">For information about SQL generation for select statements, see [SQL Generation](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span></span>  
  
## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="542f5-106">変更コマンド ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="542f5-106">Overview of Modification Command Trees</span></span>  
 <span data-ttu-id="542f5-107">変更 SQL 生成モジュールは、指定された入力 DbModificationCommandTree に基づいて、データベースに固有の変更 SQL ステートメントを生成します。</span><span class="sxs-lookup"><span data-stu-id="542f5-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="542f5-108">DbModificationCommandTree は、DbCommandTree から継承される変更 DML 操作 (挿入、更新、または削除操作) のオブジェクト モデル表現です。</span><span class="sxs-lookup"><span data-stu-id="542f5-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="542f5-109">DbModificationCommandTree には、次の 3 つの実装があります。</span><span class="sxs-lookup"><span data-stu-id="542f5-109">There are three implementations of DbModificationCommandTree:</span></span>  
  
-   <span data-ttu-id="542f5-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="542f5-110">DbInsertCommandTree</span></span>  
  
-   <span data-ttu-id="542f5-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="542f5-111">DbUpdateCommandTree</span></span>  
  
-   <span data-ttu-id="542f5-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="542f5-112">DbDeleteCommandTree</span></span>  
  
 <span data-ttu-id="542f5-113">DbModificationCommandTree とその実装によって生成される、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]常に単一行の操作を表します。</span><span class="sxs-lookup"><span data-stu-id="542f5-113">DbModificationCommandTree and its implementations that are produced by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] always represent a single row operation.</span></span> <span data-ttu-id="542f5-114">ここでは、これら 3 つの種類の実装と、.NET Framework Version 3.5 における制約について説明します。</span><span class="sxs-lookup"><span data-stu-id="542f5-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>  
  
 <span data-ttu-id="542f5-115">![ダイアグラム](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="542f5-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>  
  
 <span data-ttu-id="542f5-116">DbModificationCommandTree には、変更操作のターゲット セットを表す Target プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="542f5-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="542f5-117">入力セットを定義する Target の Expression プロパティは、常に DbScanExpression です。</span><span class="sxs-lookup"><span data-stu-id="542f5-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="542f5-118">DbScanExpression は、どちらか、テーブルまたはビューを表すことができます、または一連のデータ定義クエリを使用した場合は、メタデータ プロパティの"Defining Query"、ターゲットが null 以外です。</span><span class="sxs-lookup"><span data-stu-id="542f5-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>  
  
 <span data-ttu-id="542f5-119">モデル内で定義クエリを使用してセットが定義されているが、対応する変更操作のための関数が指定されていない場合、クエリを表す DbScanExpression は、変更のターゲットとしてプロバイダーにのみ影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="542f5-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="542f5-120">プロバイダーによっては、このようなシナリオはサポートされません (たとえば、SqlClient ではサポートされません)。</span><span class="sxs-lookup"><span data-stu-id="542f5-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>  
  
 <span data-ttu-id="542f5-121">DbInsertCommandTree は、コマンド ツリーとして表現される、単一行の挿入操作を表します。</span><span class="sxs-lookup"><span data-stu-id="542f5-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 <span data-ttu-id="542f5-122">DbUpdateCommandTree は、コマンド ツリーとして表現される、単一行の更新操作を表します。</span><span class="sxs-lookup"><span data-stu-id="542f5-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>  
  
 <span data-ttu-id="542f5-123">DbDeleteCommandTree は、コマンド ツリーとして表現される、単一行の削除操作を表します。</span><span class="sxs-lookup"><span data-stu-id="542f5-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>  
  
### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="542f5-124">変更コマンド ツリーのプロパティの制限</span><span class="sxs-lookup"><span data-stu-id="542f5-124">Restrictions on Modification Command Tree Properties</span></span>  
 <span data-ttu-id="542f5-125">変更コマンド ツリーのプロパティに対して、次の情報および制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="542f5-125">The following information and restrictions apply to the modification command tree properties.</span></span>  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="542f5-126">DbInsertCommandTree および DbUpdateCommandTree の Returning</span><span class="sxs-lookup"><span data-stu-id="542f5-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="542f5-127">null 以外の場合、Returning は、コマンドがリーダーを返すことを示します。</span><span class="sxs-lookup"><span data-stu-id="542f5-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="542f5-128">null の場合、コマンドは、影響を受けた (挿入または更新された) 行の数を示すスカラー値を返します。</span><span class="sxs-lookup"><span data-stu-id="542f5-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>  
  
 <span data-ttu-id="542f5-129">Returning 値は、挿入または更新された行に基づいて返される結果の射影を指定します。</span><span class="sxs-lookup"><span data-stu-id="542f5-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="542f5-130">この値は、行を表す DbNewInstanceExpression 型である必要があります。その各引数は、対応する DbModificationCommandTree の Target への参照を表す DbVariableReferenceExpression に対する DbPropertyExpression になります。</span><span class="sxs-lookup"><span data-stu-id="542f5-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="542f5-131">Returning プロパティで使用されている DbPropertyExpressions で表されるプロパティは、常にストア生成値または計算値となります。</span><span class="sxs-lookup"><span data-stu-id="542f5-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="542f5-132">DbInsertCommandTree では、行が挿入されるテーブルの 1 つ以上のプロパティがストア生成値または計算値として指定されている (ssdl で StoreGeneratedPattern.Identity または StoreGeneratedPattern.Computed とマークされている) 場合、Returning は null ではありません。</span><span class="sxs-lookup"><span data-stu-id="542f5-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="542f5-133">DbUpdateCommandTrees では、行が更新されるテーブルの 1 つ以上のプロパティがストア計算値として指定されている (ssdl で StoreGeneratedPattern.Computed とマークされている) 場合、Returning は null ではありません。</span><span class="sxs-lookup"><span data-stu-id="542f5-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="542f5-134">DbInsertCommandTree および DbUpdateCommandTree の SetClauses</span><span class="sxs-lookup"><span data-stu-id="542f5-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="542f5-135">SetClauses は、挿入または更新操作を定義する insert set 句または update set 句のリストを指定します。</span><span class="sxs-lookup"><span data-stu-id="542f5-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 <span data-ttu-id="542f5-136">Property は、更新する必要があるプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="542f5-136">Property specifies the property that should be updated.</span></span> <span data-ttu-id="542f5-137">これは常に、対応する DbModificationCommandTree の Target への参照を表す、DbVariableReferenceExpression に対する DbPropertyExpression です。</span><span class="sxs-lookup"><span data-stu-id="542f5-137">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="542f5-138">Value は、プロパティを更新するための新しい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="542f5-138">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="542f5-139">DbConstantExpression 型または DbNullExpression 型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="542f5-139">It is either of type DbConstantExpression or DbNullExpression.</span></span>  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="542f5-140">DbUpdateCommandTree および DbDeleteCommandTree の Predicate</span><span class="sxs-lookup"><span data-stu-id="542f5-140">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>  
 <span data-ttu-id="542f5-141">Predicate は、ターゲット コレクションのどのメンバーを更新または削除する必要があるかを判定するために使用される述語を指定します。</span><span class="sxs-lookup"><span data-stu-id="542f5-141">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="542f5-142">これは、DbExpressions の次のサブセットから構成される式ツリーです。</span><span class="sxs-lookup"><span data-stu-id="542f5-142">It is an expression tree built of the following subset of DbExpressions:</span></span>  
  
-   <span data-ttu-id="542f5-143">Equals 型の DbComparisonExpression。右辺の子は以下のように制限される DbPropertyExression、左辺の子は DbConstantExpression です。</span><span class="sxs-lookup"><span data-stu-id="542f5-143">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExression as restricted below and the left child a DbConstantExpression.</span></span>  
  
-   <span data-ttu-id="542f5-144">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="542f5-144">DbConstantExpression</span></span>  
  
-   <span data-ttu-id="542f5-145">以下のように制限される、DbPropertyExpresison に対する DbIsNullExpression。</span><span class="sxs-lookup"><span data-stu-id="542f5-145">DbIsNullExpression over a DbPropertyExpresison as restricted below</span></span>  
  
-   <span data-ttu-id="542f5-146">対応する DbModificationCommandTree の Target への参照を表す、DbVariableReferenceExpression に対する DbPropertyExpression。</span><span class="sxs-lookup"><span data-stu-id="542f5-146">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
-   <span data-ttu-id="542f5-147">DbAndExpression。</span><span class="sxs-lookup"><span data-stu-id="542f5-147">DbAndExpression</span></span>  
  
-   <span data-ttu-id="542f5-148">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="542f5-148">DbNotExpression</span></span>  
  
-   <span data-ttu-id="542f5-149">DbOrExpression。</span><span class="sxs-lookup"><span data-stu-id="542f5-149">DbOrExpression</span></span>  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="542f5-150">サンプル プロバイダーでの変更 SQL 生成</span><span class="sxs-lookup"><span data-stu-id="542f5-150">Modification SQL Generation in the Sample Provider</span></span>  
 <span data-ttu-id="542f5-151">[Entity Framework サンプル プロバイダー](http://go.microsoft.com/fwlink/?LinkId=180616)をサポートする ADO.NET データ プロバイダーのコンポーネントを示しています、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="542f5-151">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="542f5-152">このサンプルは、SQL Server 2005 データベースを対象としており、System.Data.SqlClient ADO.NET 2.0 データ プロバイダーの最上位にラッパーとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="542f5-152">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="542f5-153">SQL Generation\DmlSqlGenerator.cs ファイル内にあるサンプル プロバイダーの変更 SQL 生成モジュールは、DbModificationCommandTree を入力として受け取り、単一の変更 SQL ステートメントを生成します。この後に、DbModificationCommandTree によって指定された場合にリーダーを返す SELECT ステートメントが続く場合もあります。</span><span class="sxs-lookup"><span data-stu-id="542f5-153">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="542f5-154">生成されたコマンドの構造は、対象の SQL Server データベースの影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="542f5-154">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>  
  
### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="542f5-155">ヘルパー クラス: ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="542f5-155">Helper Classes: ExpressionTranslator</span></span>  
 <span data-ttu-id="542f5-156">ExpressionTranslator は、DbExpression 型のすべての変更コマンド ツリー プロパティのための一般的な軽量のトランスレーターです。</span><span class="sxs-lookup"><span data-stu-id="542f5-156">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="542f5-157">このトランスレーターは、変更コマンド ツリーのプロパティを制限する式の型の変換のみをサポートし、特定の制約を考慮して構築されています。</span><span class="sxs-lookup"><span data-stu-id="542f5-157">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>  
  
 <span data-ttu-id="542f5-158">以降では、特定の式の型へのアクセスについて説明します (重要度の低い変換を含むノードは省略しています)。</span><span class="sxs-lookup"><span data-stu-id="542f5-158">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>  
  
### <a name="dbcomparisonexpression"></a><span data-ttu-id="542f5-159">DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="542f5-159">DbComparisonExpression</span></span>  
 <span data-ttu-id="542f5-160">preserveMemberValues を true に設定して ExpressionTranslator を構築したときに、右辺の定数が (DbNullExpression ではなく) DbConstantExpression である場合、左辺のオペランド (DbPropertyExpressions) が DbConstantExpression に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="542f5-160">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="542f5-161">これは、返される Select ステートメントを、影響を受けた行を識別するために生成する必要がある場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="542f5-161">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>  
  
### <a name="dbconstantexpression"></a><span data-ttu-id="542f5-162">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="542f5-162">DbConstantExpression</span></span>  
 <span data-ttu-id="542f5-163">アクセスされる定数のそれぞれに対して、パラメーターが作成されます。</span><span class="sxs-lookup"><span data-stu-id="542f5-163">For each visited constant a parameter is created.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="542f5-164">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="542f5-164">DbPropertyExpression</span></span>  
 <span data-ttu-id="542f5-165">DbPropertyExpression のインスタンスが常に入力テーブルを表す場合、生成によって別名が作成される状況を除き (テーブル変数が使用されたときの更新シナリオでのみこの状況が発生します)、入力に別名を指定する必要はありません。変換には既定でプロパティ名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="542f5-165">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>  
  
## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="542f5-166">挿入 SQL コマンドの生成</span><span class="sxs-lookup"><span data-stu-id="542f5-166">Generating an Insert SQL Command</span></span>  
 <span data-ttu-id="542f5-167">サンプル プロバイダーで指定されている DbInsertCommandTree に対して生成される挿入コマンドは、以下に示す 2 つの挿入テンプレートのどちらかに基づいています。</span><span class="sxs-lookup"><span data-stu-id="542f5-167">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>  
  
 <span data-ttu-id="542f5-168">1 つ目のテンプレートには、SetClauses のリストの値を受け取って挿入を実行するコマンドと、挿入された行の Returning プロパティが null 以外の場合にその Returning プロパティで指定されたプロパティを返す SELECT ステートメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="542f5-168">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="542f5-169">述語要素"\@ @ROWCOUNT > 0" は行が挿入された場合は true です。</span><span class="sxs-lookup"><span data-stu-id="542f5-169">The predicate element "\@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="542f5-170">述語要素"keyMemberI = keyValueI &#124; scope_identity()"図形は、"keyMemberI = scope_identity()"scope_identity は、identity (に挿入された最後の id 値を返すために、keyMemeberI がストア生成のキーが場合にのみストア生成の) 列です。</span><span class="sxs-lookup"><span data-stu-id="542f5-170">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemeberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="542f5-171">2 番目のテンプレートが必要となるのは、挿入操作で行の挿入を指定するとき、主キーがストア生成値であるが整数型ではないために、scope_identity() でそのキーを使用できない場合です。</span><span class="sxs-lookup"><span data-stu-id="542f5-171">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="542f5-172">このテンプレートは、複合ストア生成キーがある場合にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="542f5-172">It is also used if there is a compound store-generated key.</span></span>  
  
```  
-- second insert template  
DECLARE @generated_keys TABLE [(keyMember0, … keyMemberN)  
  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
 OUTPUT inserted.KeyMember0, …, inserted.KeyMemberN INTO @generated_keys  
 VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES  
  
[SELECT <returning_over_t>   
 FROM @generated_keys  AS g  
JOIN <target> AS t ON g.KeyMember0 = t.KeyMember0 AND … g.KeyMemberN = t.KeyMemberN  
 WHERE @@ROWCOUNT > 0  
```  
  
 <span data-ttu-id="542f5-173">サンプル プロバイダーに含まれるモデルの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="542f5-173">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="542f5-174">この例では、DbInsertCommandTree から挿入コマンドを生成しています。</span><span class="sxs-lookup"><span data-stu-id="542f5-174">It generates an insert command from a DbInsertCommandTree.</span></span>  
  
 <span data-ttu-id="542f5-175">次のコードは、Category を挿入します。</span><span class="sxs-lookup"><span data-stu-id="542f5-175">The following code inserts a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="542f5-176">このコードでは、プロバイダーに渡される次のコマンド ツリーを生成します。</span><span class="sxs-lookup"><span data-stu-id="542f5-176">This code produces the following command tree, which is passed to the provider:</span></span>  
  
```  
DbInsertCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_SetClauses  
| |_DbSetClause  
| | |_Property  
| | | |_Var(target).CategoryName  
| | |_Value  
| |   |_'Test Category'  
| |_DbSetClause  
| | |_Property  
| | | |_Var(target).Description  
| | |_Value  
| |   |_'A new category for testing'  
| |_DbSetClause  
|   |_Property  
|   | |_Var(target).Picture  
|   |_Value  
|     |_null  
|_Returning  
  |_NewInstance : Record['CategoryID'=Edm.Int32]  
    |_Column : 'CategoryID'  
      |_Var(target).CategoryID  
```  
  
 <span data-ttu-id="542f5-177">サンプル プロバイダーによって生成されるストア コマンドは、次の SQL ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="542f5-177">The store command that the sample provider produces is the following SQL statement:</span></span>  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a><span data-ttu-id="542f5-178">更新 SQL コマンドの生成</span><span class="sxs-lookup"><span data-stu-id="542f5-178">Generating an Update SQL Command</span></span>  
 <span data-ttu-id="542f5-179">指定された DbUpdateCommandTree に対して、以下に示すテンプレートに基づいて、更新コマンドが生成されます。</span><span class="sxs-lookup"><span data-stu-id="542f5-179">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="542f5-180">Set 句が偽の set 句 ("@i = 0") set 句が指定されていない場合にのみです。</span><span class="sxs-lookup"><span data-stu-id="542f5-180">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="542f5-181">これは、ストア計算列が再計算されるようにするためです。</span><span class="sxs-lookup"><span data-stu-id="542f5-181">This is to ensure that any store-computed columns are recomputed.</span></span>  
  
 <span data-ttu-id="542f5-182">Returning プロパティが null でない場合にのみ、SELECT ステートメントが生成され、Returning プロパティに指定されたプロパティが返されます。</span><span class="sxs-lookup"><span data-stu-id="542f5-182">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>  
  
 <span data-ttu-id="542f5-183">次の例では、サンプル プロバイダーに含まれるモデルを使用して、更新コマンドを生成します。</span><span class="sxs-lookup"><span data-stu-id="542f5-183">The following example uses the model that is included with the sample provider to generate an update command.</span></span>  
  
 <span data-ttu-id="542f5-184">次のユーザー コードは、Category を更新します。</span><span class="sxs-lookup"><span data-stu-id="542f5-184">The following user code updates a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="542f5-185">このユーザー コードは、プロバイダーに渡される次のコマンド ツリーを生成します。</span><span class="sxs-lookup"><span data-stu-id="542f5-185">This user code produces the following command tree, which is passed to the provider:</span></span>  
  
```  
DbUpdateCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_SetClauses  
| |_DbSetClause  
|   |_Property  
|   | |_Var(target).CategoryName  
|   |_Value  
|     |_'New test name'  
|_Predicate  
| |_  
|   |_Var(target).CategoryID  
|   |_=  
|   |_10  
|_Returning   
```  
  
 <span data-ttu-id="542f5-186">サンプル プロバイダーによって、次のストア コマンドが生成されます。</span><span class="sxs-lookup"><span data-stu-id="542f5-186">The sample provider produces the following store command:</span></span>  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="542f5-187">削除 SQL コマンドの生成</span><span class="sxs-lookup"><span data-stu-id="542f5-187">Generating a Delete SQL Command</span></span>  
 <span data-ttu-id="542f5-188">指定された DbDeleteCommandTree に対して、以下に示すテンプレートに基づいて、削除コマンドが生成されます。</span><span class="sxs-lookup"><span data-stu-id="542f5-188">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 <span data-ttu-id="542f5-189">次の例では、サンプル プロバイダーに含まれるモデルを使用して、削除コマンドを生成します。</span><span class="sxs-lookup"><span data-stu-id="542f5-189">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>  
  
 <span data-ttu-id="542f5-190">次のユーザー コードは、Category を削除します。</span><span class="sxs-lookup"><span data-stu-id="542f5-190">The following user code deletes a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="542f5-191">このユーザー コードは、プロバイダーに渡される次のコマンド ツリーを生成します。</span><span class="sxs-lookup"><span data-stu-id="542f5-191">This user code produces the following command tree, which is passed to the provider.</span></span>  
  
```  
DbDeleteCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_Predicate  
  |_  
    |_Var(target).CategoryID  
    |_=  
    |_10  
```  
  
 <span data-ttu-id="542f5-192">サンプル プロバイダーによって、次のストア コマンドが生成されます。</span><span class="sxs-lookup"><span data-stu-id="542f5-192">The following store command is produced by the sample provider:</span></span>  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a><span data-ttu-id="542f5-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="542f5-193">See Also</span></span>  
 [<span data-ttu-id="542f5-194">Entity Framework データ プロバイダーの作成</span><span class="sxs-lookup"><span data-stu-id="542f5-194">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
