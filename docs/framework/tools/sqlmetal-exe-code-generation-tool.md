---
title: "SqlMetal.exe (コード生成ツール)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
caps.latest.revision: 43
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6d0ac9c682c60db8eb9e5188a71916dc5d97de60
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="6337d-102">SqlMetal.exe (コード生成ツール)</span><span class="sxs-lookup"><span data-stu-id="6337d-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="6337d-103">SqlMetal コマンド ライン ツールは、 [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] の [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]コンポーネント用のコードとマッピングを生成します。</span><span class="sxs-lookup"><span data-stu-id="6337d-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="6337d-104">このトピックで後述するオプションを適用することにより、次のようなアクションを SqlMetal で実行できます。</span><span class="sxs-lookup"><span data-stu-id="6337d-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
-   <span data-ttu-id="6337d-105">データベースから、ソース コードとマッピング属性またはマッピング ファイルを生成する。</span><span class="sxs-lookup"><span data-stu-id="6337d-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
-   <span data-ttu-id="6337d-106">データベースから、カスタマイズ用の中間的なデータベース マークアップ言語 (.dbml) ファイルを生成する。</span><span class="sxs-lookup"><span data-stu-id="6337d-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
-   <span data-ttu-id="6337d-107">.dbml ファイルから、コードとマッピング属性またはマッピング ファイルを生成する。</span><span class="sxs-lookup"><span data-stu-id="6337d-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="6337d-108">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="6337d-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="6337d-109">既定では、このファイルは `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin にあります。</span><span class="sxs-lookup"><span data-stu-id="6337d-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="6337d-110">Visual Studio をインストールしない場合は、 [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225)をダウンロードすることによって SQLMetal ファイルを入手することもできます。</span><span class="sxs-lookup"><span data-stu-id="6337d-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6337d-111">Visual Studio を使用している開発者は、 [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] を使ってエンティティ クラスを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="6337d-111">Developers who use Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] to generate entity classes.</span></span> <span data-ttu-id="6337d-112">コマンド ライン方式は、大きなデータベースにも適切に対応できます。</span><span class="sxs-lookup"><span data-stu-id="6337d-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="6337d-113">SqlMetal はコマンド ライン ツールであるため、ビルド プロセスでこれを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6337d-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="6337d-114">このツールを実行するには、開発者コマンド プロンプト (または、Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="6337d-114">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="6337d-115">詳細については、「[Visual Studio 用開発者コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。コマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="6337d-115">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6337d-116">構文</span><span class="sxs-lookup"><span data-stu-id="6337d-116">Syntax</span></span>  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="6337d-117">オプション</span><span class="sxs-lookup"><span data-stu-id="6337d-117">Options</span></span>  
 <span data-ttu-id="6337d-118">最新のオプションの一覧を確認するには、コマンド プロンプトでインストール場所に移動し、「 `sqlmetal /?` 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="6337d-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="6337d-119">**接続オプション**</span><span class="sxs-lookup"><span data-stu-id="6337d-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="6337d-120">オプション</span><span class="sxs-lookup"><span data-stu-id="6337d-120">Option</span></span>|<span data-ttu-id="6337d-121">説明</span><span class="sxs-lookup"><span data-stu-id="6337d-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6337d-122">**/server:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="6337d-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="6337d-123">データベース サーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="6337d-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="6337d-124">**/database:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="6337d-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="6337d-125">サーバー上のデータベース カタログを指定します。</span><span class="sxs-lookup"><span data-stu-id="6337d-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="6337d-126">**/user:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="6337d-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="6337d-127">ログオン ユーザー ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="6337d-127">Specifies logon user id.</span></span> <span data-ttu-id="6337d-128">既定値は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="6337d-128">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="6337d-129">**/password:** *\<password>*</span><span class="sxs-lookup"><span data-stu-id="6337d-129">**/password:** *\<password>*</span></span>|<span data-ttu-id="6337d-130">ログオン パスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="6337d-130">Specifies logon password.</span></span> <span data-ttu-id="6337d-131">既定値は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="6337d-131">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="6337d-132">**/conn:** *\<connection string>*</span><span class="sxs-lookup"><span data-stu-id="6337d-132">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="6337d-133">データベース接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="6337d-133">Specifies database connection string.</span></span> <span data-ttu-id="6337d-134">**/server**、 **/database**、 **/user**、または **/password** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="6337d-134">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="6337d-135">接続文字列にファイル名は含めないでください。</span><span class="sxs-lookup"><span data-stu-id="6337d-135">Do not include the file name in the connection string.</span></span> <span data-ttu-id="6337d-136">代わりに、コマンド ラインにファイル名を入力ファイルとして追加します。</span><span class="sxs-lookup"><span data-stu-id="6337d-136">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="6337d-137">たとえば、 **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**というコマンド ラインは、入力ファイルとして "c:\northwnd.mdf" を指定します。</span><span class="sxs-lookup"><span data-stu-id="6337d-137">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="6337d-138">**/timeout:** *\<seconds>*</span><span class="sxs-lookup"><span data-stu-id="6337d-138">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="6337d-139">SqlMetal がデータベースにアクセスする際のタイムアウト値を指定します。</span><span class="sxs-lookup"><span data-stu-id="6337d-139">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="6337d-140">既定値は 0 (時間制限なし) です。</span><span class="sxs-lookup"><span data-stu-id="6337d-140">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="6337d-141">**抽出オプション**</span><span class="sxs-lookup"><span data-stu-id="6337d-141">**Extraction options**</span></span>  
  
|<span data-ttu-id="6337d-142">オプション</span><span class="sxs-lookup"><span data-stu-id="6337d-142">Option</span></span>|<span data-ttu-id="6337d-143">説明</span><span class="sxs-lookup"><span data-stu-id="6337d-143">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6337d-144">**/views**</span><span class="sxs-lookup"><span data-stu-id="6337d-144">**/views**</span></span>|<span data-ttu-id="6337d-145">データベース ビューを抽出します。</span><span class="sxs-lookup"><span data-stu-id="6337d-145">Extracts database views.</span></span>|  
|<span data-ttu-id="6337d-146">**/functions**</span><span class="sxs-lookup"><span data-stu-id="6337d-146">**/functions**</span></span>|<span data-ttu-id="6337d-147">データベース関数を抽出します。</span><span class="sxs-lookup"><span data-stu-id="6337d-147">Extracts database functions.</span></span>|  
|<span data-ttu-id="6337d-148">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="6337d-148">**/sprocs**</span></span>|<span data-ttu-id="6337d-149">ストアド プロシージャを抽出します。</span><span class="sxs-lookup"><span data-stu-id="6337d-149">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="6337d-150">**出力オプション**</span><span class="sxs-lookup"><span data-stu-id="6337d-150">**Output options**</span></span>  
  
|<span data-ttu-id="6337d-151">オプション</span><span class="sxs-lookup"><span data-stu-id="6337d-151">Option</span></span>|<span data-ttu-id="6337d-152">説明</span><span class="sxs-lookup"><span data-stu-id="6337d-152">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6337d-153">**/dbml** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="6337d-153">**/dbml** *[:file]*</span></span>|<span data-ttu-id="6337d-154">出力を .dbml として送ります。</span><span class="sxs-lookup"><span data-stu-id="6337d-154">Sends output as .dbml.</span></span> <span data-ttu-id="6337d-155">**/map** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="6337d-155">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="6337d-156">**/code** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="6337d-156">**/code** *[:file]*</span></span>|<span data-ttu-id="6337d-157">出力をソース コードとして送ります。</span><span class="sxs-lookup"><span data-stu-id="6337d-157">Sends output as source code.</span></span> <span data-ttu-id="6337d-158">**/dbml** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="6337d-158">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="6337d-159">**/map** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="6337d-159">**/map** *[:file]*</span></span>|<span data-ttu-id="6337d-160">属性ではなく XML マッピング ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="6337d-160">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="6337d-161">**/dbml** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="6337d-161">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="6337d-162">**その他**</span><span class="sxs-lookup"><span data-stu-id="6337d-162">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="6337d-163">オプション</span><span class="sxs-lookup"><span data-stu-id="6337d-163">Option</span></span>|<span data-ttu-id="6337d-164">説明</span><span class="sxs-lookup"><span data-stu-id="6337d-164">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6337d-165">**/language:** *\<language>*</span><span class="sxs-lookup"><span data-stu-id="6337d-165">**/language:** *\<language>*</span></span>|<span data-ttu-id="6337d-166">ソース コードの言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="6337d-166">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="6337d-167">Valid *\<language>*: vb, csharp.</span><span class="sxs-lookup"><span data-stu-id="6337d-167">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="6337d-168">既定値は、コード ファイル名の拡張子から派生します。</span><span class="sxs-lookup"><span data-stu-id="6337d-168">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="6337d-169">**/namespace:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="6337d-169">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="6337d-170">生成されるコードの名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="6337d-170">Specifies namespace of the generated code.</span></span> <span data-ttu-id="6337d-171">既定値は、名前空間なしです。</span><span class="sxs-lookup"><span data-stu-id="6337d-171">Default value: no namespace.</span></span>|  
|<span data-ttu-id="6337d-172">**/context:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="6337d-172">**/context:** *\<type>*</span></span>|<span data-ttu-id="6337d-173">データ コンテキスト クラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="6337d-173">Specifies name of data context class.</span></span> <span data-ttu-id="6337d-174">既定値は、データベース名から派生します。</span><span class="sxs-lookup"><span data-stu-id="6337d-174">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="6337d-175">**/entitybase:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="6337d-175">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="6337d-176">生成されるコード内のエンティティ クラスの基本クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="6337d-176">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="6337d-177">既定値は、エンティティの基本クラスなしです。</span><span class="sxs-lookup"><span data-stu-id="6337d-177">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="6337d-178">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="6337d-178">**/pluralize**</span></span>|<span data-ttu-id="6337d-179">クラスとメンバーの名前を自動的に複数化または単数化します。</span><span class="sxs-lookup"><span data-stu-id="6337d-179">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="6337d-180">このオプションは、米国英語バージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="6337d-180">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="6337d-181">**/serialization:** *\<option>*</span><span class="sxs-lookup"><span data-stu-id="6337d-181">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="6337d-182">シリアル化可能なクラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="6337d-182">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="6337d-183">Valid *\<option>*: Non、Unidirectional。</span><span class="sxs-lookup"><span data-stu-id="6337d-183">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="6337d-184">既定値は None です。</span><span class="sxs-lookup"><span data-stu-id="6337d-184">Default value: None.</span></span><br /><br /> <span data-ttu-id="6337d-185">詳細については、「[Serialization](../../../docs/framework/data/adonet/sql/linq/serialization.md)」 (シリアル化) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6337d-185">For more information, see [Serialization](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="6337d-186">**入力ファイル**</span><span class="sxs-lookup"><span data-stu-id="6337d-186">**Input File**</span></span>  
  
|<span data-ttu-id="6337d-187">オプション</span><span class="sxs-lookup"><span data-stu-id="6337d-187">Option</span></span>|<span data-ttu-id="6337d-188">説明</span><span class="sxs-lookup"><span data-stu-id="6337d-188">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6337d-189">**\<入力ファイル>**</span><span class="sxs-lookup"><span data-stu-id="6337d-189">**\<input file>**</span></span>|<span data-ttu-id="6337d-190">SQL Server Express .mdf ファイル、 [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf ファイル、または .dbml 中間ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="6337d-190">Specifies a SQL Server Express .mdf file, a [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6337d-191">コメント</span><span class="sxs-lookup"><span data-stu-id="6337d-191">Remarks</span></span>  
 <span data-ttu-id="6337d-192">SqlMetal の実際の機能には、次の 2 つの段階が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6337d-192">SqlMetal functionality actually involves two steps:</span></span>  
  
-   <span data-ttu-id="6337d-193">データベースのメタデータを .dbml ファイルに抽出する。</span><span class="sxs-lookup"><span data-stu-id="6337d-193">Extracting the metadata of the database into a .dbml file.</span></span>  
  
-   <span data-ttu-id="6337d-194">コード出力ファイルを生成する。</span><span class="sxs-lookup"><span data-stu-id="6337d-194">Generating a code output file.</span></span>  
  
     <span data-ttu-id="6337d-195">適切なコマンド ライン オプションを使用することで、 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] または C# ソース コードを生成するか、XML マッピング ファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="6337d-195">By using the appropriate command-line options, you can produce [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="6337d-196">メタデータを .mdf ファイルから抽出するには、他のすべてのオプションの後に .mdf ファイルの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6337d-196">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="6337d-197">**/server** を指定しない場合、 **localhost/sqlexpress** と見なされます。</span><span class="sxs-lookup"><span data-stu-id="6337d-197">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="6337d-198">次の条件が少なくとも 1 つ満たされる場合、[!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)] は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="6337d-198">[!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)] throws an exception if one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="6337d-199">自身を呼び出すストアド プロシージャを SqlMetal が抽出しようとした。</span><span class="sxs-lookup"><span data-stu-id="6337d-199">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
-   <span data-ttu-id="6337d-200">ストアド プロシージャ、関数、またはビューの入れ子レベルが 32 を超える。</span><span class="sxs-lookup"><span data-stu-id="6337d-200">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="6337d-201">SqlMetal はこの例外をキャッチして、それを警告として報告します。</span><span class="sxs-lookup"><span data-stu-id="6337d-201">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="6337d-202">入力ファイル名を指定するには、その名前をコマンド ラインに入力ファイルとして追加します。</span><span class="sxs-lookup"><span data-stu-id="6337d-202">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="6337d-203">( **/conn** オプションを使用して) 接続文字列にファイル名を含める操作は、サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6337d-203">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6337d-204">例</span><span class="sxs-lookup"><span data-stu-id="6337d-204">Examples</span></span>  
 <span data-ttu-id="6337d-205">抽出された SQL メタデータを格納する .dbml ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="6337d-205">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="6337d-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="6337d-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="6337d-207">SQL Server Express を使用して .mdf ファイルから抽出された SQL メタデータを格納する .dbml ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="6337d-207">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="6337d-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="6337d-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="6337d-209">SQL Server Express から抽出された SQL メタデータを格納する .dbml ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="6337d-209">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="6337d-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="6337d-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="6337d-211">.dbml メタデータ ファイルからソース コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="6337d-211">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="6337d-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="6337d-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="6337d-213">SQL メタデータからソース コードを直接生成します。</span><span class="sxs-lookup"><span data-stu-id="6337d-213">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="6337d-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="6337d-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6337d-215">サンプル データベース Northwind で **/pluralize** オプションを使用する場合には、注意を必要とする動作があります。</span><span class="sxs-lookup"><span data-stu-id="6337d-215">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="6337d-216">SqlMetal がテーブルのために行型の名前を生成するとき、テーブル名は単数形です。</span><span class="sxs-lookup"><span data-stu-id="6337d-216">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="6337d-217">テーブルに関する <xref:System.Data.Linq.DataContext> プロパティを生成するときには、テーブル名は複数形です。</span><span class="sxs-lookup"><span data-stu-id="6337d-217">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="6337d-218">偶然にも、サンプル データベース Northwind 内のテーブルには既に複数形が使われています。</span><span class="sxs-lookup"><span data-stu-id="6337d-218">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="6337d-219">このため、この部分はうまく機能しません。</span><span class="sxs-lookup"><span data-stu-id="6337d-219">Therefore, you do not see that part working.</span></span> <span data-ttu-id="6337d-220">データベース テーブルの名前は単数形にするのが一般的ですが、.NET では、コレクションの名前を複数形にすることも一般的です。</span><span class="sxs-lookup"><span data-stu-id="6337d-220">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6337d-221">関連項目</span><span class="sxs-lookup"><span data-stu-id="6337d-221">See Also</span></span>  
 <span data-ttu-id="6337d-222">[方法: Visual Basic または C# でオブジェクト モデルを生成する](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md) </span><span class="sxs-lookup"><span data-stu-id="6337d-222">[How to: Generate the Object Model in Visual Basic or C#](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md) </span></span>  
 <span data-ttu-id="6337d-223">[LINQ to SQL でのコード生成](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md) </span><span class="sxs-lookup"><span data-stu-id="6337d-223">[Code Generation in LINQ to SQL](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md) </span></span>  
 [<span data-ttu-id="6337d-224">外部マップ</span><span class="sxs-lookup"><span data-stu-id="6337d-224">External Mapping</span></span>](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)

