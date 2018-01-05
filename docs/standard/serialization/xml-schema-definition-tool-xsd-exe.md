---
title: XML Schema Definition Tool (Xsd.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0e6407fc8da8695da47165ae0ea2c2c6d863ec23
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="xml-schema-definition-tool-xsdexe"></a><span data-ttu-id="7bc53-102">XML Schema Definition Tool (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="7bc53-102">XML Schema Definition Tool (Xsd.exe)</span></span>
<span data-ttu-id="7bc53-103">XML スキーマ定義ツール (Xsd.exe) は、XDR、XML、および XSD ファイル、またはランタイム アセンブリ内のクラスから XML スキーマ クラスまたは共通言語ランタイム クラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-103">The XML Schema Definition (Xsd.exe) tool generates XML schema or common language runtime classes from XDR, XML, and XSD files, or from classes in a runtime assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bc53-104">構文</span><span class="sxs-lookup"><span data-stu-id="7bc53-104">Syntax</span></span>  
  
```  
xsd file.xdr [/outputdir:directory][/parameters:file.xml]  
xsd file.xml [/outputdir:directory] [/parameters:file.xml]  
xsd file.xsd {/classes | /dataset} [/element:element]   
             [/enableLinqDataSet] [/language:language]   
                          [/namespace:namespace] [/outputdir:directory] [URI:uri]   
                          [/parameters:file.xml]  
xsd {file.dll | file.exe} [/outputdir:directory] [/type:typename [...]][/parameters:file.xml]  
```  
  
## <a name="argument"></a><span data-ttu-id="7bc53-105">引数</span><span class="sxs-lookup"><span data-stu-id="7bc53-105">Argument</span></span>  
  
|<span data-ttu-id="7bc53-106">引数</span><span class="sxs-lookup"><span data-stu-id="7bc53-106">Argument</span></span>|<span data-ttu-id="7bc53-107">説明</span><span class="sxs-lookup"><span data-stu-id="7bc53-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="7bc53-108">*file.extension*</span><span class="sxs-lookup"><span data-stu-id="7bc53-108">*file.extension*</span></span>|<span data-ttu-id="7bc53-109">変換元の入力ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-109">Specifies the input file to convert.</span></span> <span data-ttu-id="7bc53-110">拡張子として、.xdr、.xml、.xsd、.dll、または .exe のいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-110">You must specify the extensionas one of the following: .xdr, .xml, .xsd, .dll, or .exe.</span></span><br /><br /> <span data-ttu-id="7bc53-111">XDR スキーマ ファイル (拡張子 .xdr) を指定すると、Xsd.exe は XDR スキーマを XSD スキーマに変換します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-111">If you specify an XDR schema file (.xdr extension), Xsd.exe converts the XDR schema to an XSD schema.</span></span> <span data-ttu-id="7bc53-112">出力ファイルの名前は XDR スキーマと同じですが、拡張子は .xsd となります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-112">The output file has the same name as the XDR schema, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="7bc53-113">XML ファイル (拡張子 .xml) を指定すると、Xsd.exe はそのファイル内のデータからスキーマを推測して XSD スキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-113">If you specify an XML file (.xml extension), Xsd.exe infers a schema from the data in the file and produces an XSD schema.</span></span> <span data-ttu-id="7bc53-114">出力ファイルの名前は XML ファイルと同じですが、拡張子は .xsd となります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-114">The output file has the same name as the XML file, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="7bc53-115">XML スキーマ ファイル (拡張子 .xsd) を指定すると、XML スキーマと対応するランタイム オブジェクト用のソース コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-115">If you specify an XML schema file (.xsd extension), Xsd.exe generates source code for runtime objects that correspond to the XML schema.</span></span><br /><br /> <span data-ttu-id="7bc53-116">ランタイム アセンブリ ファイル (拡張子 .exe または .dll) を指定すると、そのアセンブリに含まれる 1 つ以上の型用のスキーマが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-116">If you specify a runtime assembly file (.exe or .dll extension), Xsd.exe generates schemas for one or more types in that assembly.</span></span> <span data-ttu-id="7bc53-117">`/type` オプションを使用して、スキーマを生成する対象の型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-117">You can use the `/type` option to specify the types for which to generate schemas.</span></span> <span data-ttu-id="7bc53-118">出力スキーマには、schema0.xsd、schema1.xsd などの名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-118">The output schemas are named schema0.xsd, schema1.xsd, and so on.</span></span> <span data-ttu-id="7bc53-119">Xsd.exe が複数のスキーマを生成するのは、指定した型によって、カスタム属性 `XMLRoot` を使用する名前空間が特定される場合のみです。</span><span class="sxs-lookup"><span data-stu-id="7bc53-119">Xsd.exe produces multiple schemas only if the given types specify a namespace using the `XMLRoot` custom attribute.</span></span>|  
  
## <a name="general-options"></a><span data-ttu-id="7bc53-120">一般オプション</span><span class="sxs-lookup"><span data-stu-id="7bc53-120">General Options</span></span>  
  
|<span data-ttu-id="7bc53-121">オプション</span><span class="sxs-lookup"><span data-stu-id="7bc53-121">Option</span></span>|<span data-ttu-id="7bc53-122">説明</span><span class="sxs-lookup"><span data-stu-id="7bc53-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7bc53-123">**/h****[elp]**</span><span class="sxs-lookup"><span data-stu-id="7bc53-123">**/h**[**elp**]</span></span>|<span data-ttu-id="7bc53-124">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-124">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="7bc53-125">**/o****[utputdir]****:***directory*</span><span class="sxs-lookup"><span data-stu-id="7bc53-125">**/o**[**utputdir**]**:***directory*</span></span>|<span data-ttu-id="7bc53-126">出力ファイル用のディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-126">Specifies the directory for output files.</span></span> <span data-ttu-id="7bc53-127">この引数は 1 回だけ指定できます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-127">This argument can appear only once.</span></span> <span data-ttu-id="7bc53-128">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="7bc53-128">The default is the current directory.</span></span>|  
|<span data-ttu-id="7bc53-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="7bc53-129">**/?**</span></span>|<span data-ttu-id="7bc53-130">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="7bc53-131">**/P[arameters]:** *file.xml*</span><span class="sxs-lookup"><span data-stu-id="7bc53-131">**/P[arameters]:** *file.xml*</span></span>|<span data-ttu-id="7bc53-132">指定された .xml ファイルから各種のオペレーション モードのためのオプションを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-132">Read options for various operation modes from the specified .xml file.</span></span> <span data-ttu-id="7bc53-133">省略形は '/p:' です。</span><span class="sxs-lookup"><span data-stu-id="7bc53-133">The short form is '/p:'.</span></span> <span data-ttu-id="7bc53-134">詳細については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bc53-134">For more information, see the following Remarks section.</span></span>|  
  
## <a name="xsd-file-options"></a><span data-ttu-id="7bc53-135">XSD ファイルのオプション</span><span class="sxs-lookup"><span data-stu-id="7bc53-135">XSD File Options</span></span>  
 <span data-ttu-id="7bc53-136">.xsd ファイルについては、次のオプションのうち 1 つだけを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-136">You must specify only one of the following options for .xsd files.</span></span>  
  
|<span data-ttu-id="7bc53-137">オプション</span><span class="sxs-lookup"><span data-stu-id="7bc53-137">Option</span></span>|<span data-ttu-id="7bc53-138">説明</span><span class="sxs-lookup"><span data-stu-id="7bc53-138">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7bc53-139">**/c****[lasses]**</span><span class="sxs-lookup"><span data-stu-id="7bc53-139">**/c**[**lasses**]</span></span>|<span data-ttu-id="7bc53-140">指定したスキーマと対応するクラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-140">Generates classes that correspond to the specified schema.</span></span> <span data-ttu-id="7bc53-141">オブジェクトに XML データを読み込むには、`System.Xml.Serialization.XmlSerializer.Deserializer` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-141">To read XML data into the object, use the `System.Xml.Serialization.XmlSerializer.Deserializer` method.</span></span>|  
|<span data-ttu-id="7bc53-142">**/d****[ataset]**</span><span class="sxs-lookup"><span data-stu-id="7bc53-142">**/d**[**ataset**]</span></span>|<span data-ttu-id="7bc53-143">指定したスキーマに対応する <xref:System.Data.DataSet> から派生したクラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-143">Generates a class derived from <xref:System.Data.DataSet> that corresponds to the specified schema.</span></span> <span data-ttu-id="7bc53-144">派生したクラスに XML データを読み込むには、`System.Data.DataSet.ReadXml` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-144">To read XML data into the derived class, use the `System.Data.DataSet.ReadXml` method.</span></span>|  
  
 <span data-ttu-id="7bc53-145">.xsd ファイルについては、次のオプションのうち任意のオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-145">You can also specify any of the following options for .xsd files.</span></span>  
  
|<span data-ttu-id="7bc53-146">オプション</span><span class="sxs-lookup"><span data-stu-id="7bc53-146">Option</span></span>|<span data-ttu-id="7bc53-147">説明</span><span class="sxs-lookup"><span data-stu-id="7bc53-147">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7bc53-148">**/e****[lement]****:***element*</span><span class="sxs-lookup"><span data-stu-id="7bc53-148">**/e**[**lement**]**:***element*</span></span>|<span data-ttu-id="7bc53-149">コードを生成する対象とする、スキーマ内の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-149">Specifies the element in the schema to generate code for.</span></span> <span data-ttu-id="7bc53-150">既定では、すべての要素が指定されます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-150">By default all elements are typed.</span></span> <span data-ttu-id="7bc53-151">この引数は、複数回指定できます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-151">You can specify this argument more than once.</span></span>|  
|<span data-ttu-id="7bc53-152">**/enableDataBinding**</span><span class="sxs-lookup"><span data-stu-id="7bc53-152">**/enableDataBinding**</span></span>|<span data-ttu-id="7bc53-153">データ バインディングを有効にするために、生成されたすべての型に <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-153">Implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface on all generated types to enable data binding.</span></span> <span data-ttu-id="7bc53-154">短縮形は `/edb` です。</span><span class="sxs-lookup"><span data-stu-id="7bc53-154">The short form is `/edb`.</span></span>|  
|<span data-ttu-id="7bc53-155">**/enableLinqDataSet**</span><span class="sxs-lookup"><span data-stu-id="7bc53-155">**/enableLinqDataSet**</span></span>|<span data-ttu-id="7bc53-156">(短縮形 : `/eld`)。LINQ to DataSet を使用して、生成された DataSet を照会できるように指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-156">(Short form: `/eld`.) Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="7bc53-157">このオプションは /dataset オプションも指定した場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-157">This option is used when the /dataset option is also specified.</span></span> <span data-ttu-id="7bc53-158">詳細については、「[LINQ to DataSet Overview](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)」(LINQ to DataSet Overview) と「[Querying Typed DataSets](../../../docs/framework/data/adonet/querying-typed-datasets.md)」(型指定された DataSet のクエリ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bc53-158">For more information, see [LINQ to DataSet Overview](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) and [Querying Typed DataSets](../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="7bc53-159">LINQ の詳細については、「[統合言語クエリ (LINQ)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bc53-159">For general information about using LINQ, see [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span>|  
|<span data-ttu-id="7bc53-160">**/f****[ields]**</span><span class="sxs-lookup"><span data-stu-id="7bc53-160">**/f**[**ields**]</span></span>|<span data-ttu-id="7bc53-161">プロパティの代わりにフィールドを生成します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-161">Generates fields instead of properties.</span></span> <span data-ttu-id="7bc53-162">既定では、プロパティが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-162">By default, properties are generated.</span></span>|  
|<span data-ttu-id="7bc53-163">**/l****[anguage]****:***language*</span><span class="sxs-lookup"><span data-stu-id="7bc53-163">**/l**[**anguage**]**:***language*</span></span>|<span data-ttu-id="7bc53-164">使用するプログラミング言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-164">Specifies the programming language to use.</span></span> <span data-ttu-id="7bc53-165">`CS` (C#、既定値)、`VB` (Visual Basic)、`JS` (JScript)、または `VJS` (Visual J#) から選択します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-165">Choose from `CS` (C#, which is the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="7bc53-166"><xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> を実装するクラスの完全修飾名を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-166">You can also specify a fully qualified name for a class implementing <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span></span>|  
|<span data-ttu-id="7bc53-167">**/n****[amespace]****:***namespace*</span><span class="sxs-lookup"><span data-stu-id="7bc53-167">**/n**[**amespace**]**:***namespace*</span></span>|<span data-ttu-id="7bc53-168">生成する型のランタイム名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-168">Specifies the runtime namespace for the generated types.</span></span> <span data-ttu-id="7bc53-169">既定の名前空間は `Schemas` です。</span><span class="sxs-lookup"><span data-stu-id="7bc53-169">The default namespace is `Schemas`.</span></span>|  
|<span data-ttu-id="7bc53-170">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="7bc53-170">**/nologo**</span></span>|<span data-ttu-id="7bc53-171">バナーを表示しません。</span><span class="sxs-lookup"><span data-stu-id="7bc53-171">Suppresses the banner.</span></span>|  
|<span data-ttu-id="7bc53-172">**/order**</span><span class="sxs-lookup"><span data-stu-id="7bc53-172">**/order**</span></span>|<span data-ttu-id="7bc53-173">すべてのパーティクル メンバーに明示的な順序 ID を生成します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-173">Generates explicit order identifiers on all particle members.</span></span>|  
|<span data-ttu-id="7bc53-174">**/o[ut]:** *directoryName*</span><span class="sxs-lookup"><span data-stu-id="7bc53-174">**/o[ut]:** *directoryName*</span></span>|<span data-ttu-id="7bc53-175">ファイルを格納する出力ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-175">Specifies the output directory to place the files in.</span></span> <span data-ttu-id="7bc53-176">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="7bc53-176">The default is the current directory.</span></span>|  
|<span data-ttu-id="7bc53-177">**/u****[ri]****:***uri*</span><span class="sxs-lookup"><span data-stu-id="7bc53-177">**/u**[**ri**]**:***uri*</span></span>|<span data-ttu-id="7bc53-178">コードを生成する対象とする、スキーマ内の要素の URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-178">Specifies the URI for the elements in the schema to generate code for.</span></span> <span data-ttu-id="7bc53-179">指定した場合、この URI は `/element` オプションで指定したすべての要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-179">This URI, if present, applies to all elements specified with the `/element` option.</span></span>|  
  
## <a name="dll-and-exe-file-options"></a><span data-ttu-id="7bc53-180">DLL ファイルと EXE ファイルのオプション</span><span class="sxs-lookup"><span data-stu-id="7bc53-180">DLL and EXE File Options</span></span>  
  
|<span data-ttu-id="7bc53-181">オプション</span><span class="sxs-lookup"><span data-stu-id="7bc53-181">Option</span></span>|<span data-ttu-id="7bc53-182">説明</span><span class="sxs-lookup"><span data-stu-id="7bc53-182">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7bc53-183">**/t****[ype]****:***typename*</span><span class="sxs-lookup"><span data-stu-id="7bc53-183">**/t**[**ype**]**:***typename*</span></span>|<span data-ttu-id="7bc53-184">スキーマの作成対象とする型の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-184">Specifies the name of the type to create a schema for.</span></span> <span data-ttu-id="7bc53-185">複数の型の引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-185">You can specify multiple type arguments.</span></span> <span data-ttu-id="7bc53-186">*typename* によって名前空間が特定されない場合、指定された型を持つアセンブリに含まれるすべての型が対象となります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-186">If *typename* does not specify a namespace, Xsd.exe matches all types in the assembly with the specified type.</span></span> <span data-ttu-id="7bc53-187">*typename* によって名前空間が特定される場合は、その型だけが対象になります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-187">If *typename* specifies a namespace, only that type is matched.</span></span> <span data-ttu-id="7bc53-188">*typename* の末尾がアスタリスク (\*) の場合は、\* の前にある文字列で始まる型のすべてが対象となります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-188">If *typename* ends with an asterisk character (\*), the tool matches all types that start with the string preceding the \*.</span></span> <span data-ttu-id="7bc53-189">`/type` オプションを省略すると、アセンブリに含まれるすべての型についてスキーマが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-189">If you omit the `/type` option, Xsd.exe generates schemas for all types in the assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bc53-190">コメント</span><span class="sxs-lookup"><span data-stu-id="7bc53-190">Remarks</span></span>  
 <span data-ttu-id="7bc53-191">Xsd.exe が実行する操作を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-191">The following table shows the operations that Xsd.exe performs.</span></span>  
  
 <span data-ttu-id="7bc53-192">XDR から XSD へ</span><span class="sxs-lookup"><span data-stu-id="7bc53-192">XDR to XSD</span></span>  
 <span data-ttu-id="7bc53-193">XML-Data-Reduced スキーマ ファイルから XML スキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-193">Generates an XML schema from an XML-Data-Reduced schema file.</span></span> <span data-ttu-id="7bc53-194">XDR は初期の XML ベースのスキーマ形式です。</span><span class="sxs-lookup"><span data-stu-id="7bc53-194">XDR is an early XML-based schema format.</span></span>  
  
 <span data-ttu-id="7bc53-195">XML から XSD へ</span><span class="sxs-lookup"><span data-stu-id="7bc53-195">XML to XSD</span></span>  
 <span data-ttu-id="7bc53-196">XML ファイルから XML スキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-196">Generates an XML schema from an XML file.</span></span>  
  
 <span data-ttu-id="7bc53-197">XSD から DataSet へ</span><span class="sxs-lookup"><span data-stu-id="7bc53-197">XSD to DataSet</span></span>  
 <span data-ttu-id="7bc53-198">XSD スキーマ ファイルから共通言語ランタイムの <xref:System.Data.DataSet> クラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-198">Generates common language runtime <xref:System.Data.DataSet> classes from an XSD schema file.</span></span> <span data-ttu-id="7bc53-199">生成されるクラスには、標準の XML データ用のリッチ オブジェクト モデルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="7bc53-199">The generated classes provide a rich object model for regular XML data.</span></span>  
  
 <span data-ttu-id="7bc53-200">XSD からクラスへ</span><span class="sxs-lookup"><span data-stu-id="7bc53-200">XSD to Classes</span></span>  
 <span data-ttu-id="7bc53-201">XSD スキーマ ファイルからランタイム クラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-201">Generates runtime classes from an XSD schema file.</span></span> <span data-ttu-id="7bc53-202">生成されたクラスを <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> と組み合わせて使用すると、このスキーマに従う XML コードの読み書きを実行できます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-202">The generated classes can be used in conjunction with <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> to read and write XML code that follows the schema.</span></span>  
  
 <span data-ttu-id="7bc53-203">クラスから XSD へ</span><span class="sxs-lookup"><span data-stu-id="7bc53-203">Classes to XSD</span></span>  
 <span data-ttu-id="7bc53-204">ランタイム アセンブリ ファイルに含まれる 1 つ以上の型から XML スキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-204">Generates an XML schema from a type or types in a runtime assembly file.</span></span> <span data-ttu-id="7bc53-205">生成されたスキーマは、`System.Xml.Serialization.XmlSerializer` で使用される XML 形式を定義します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-205">The generated schema defines the XML format used by `System.Xml.Serialization.XmlSerializer`.</span></span>  
  
 <span data-ttu-id="7bc53-206">Xsd.exe によって操作できるのは、W3C (World Wide Web Consortium) が提唱する XSD (XML スキーマ定義) に準拠した XML スキーマだけです。</span><span class="sxs-lookup"><span data-stu-id="7bc53-206">Xsd.exe only allows you to manipulate XML schemas that follow the XML Schema Definition (XSD) language proposed by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="7bc53-207">XML スキーマ定義の提唱や XML 標準の詳細については、http://w3.org を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bc53-207">For more information on the XML Schema Definition proposal or the XML standard, see http://w3.org.</span></span>  
  
## <a name="setting-options-with-an-xml-file"></a><span data-ttu-id="7bc53-208">XML ファイルによるオプションの設定</span><span class="sxs-lookup"><span data-stu-id="7bc53-208">Setting Options with an XML File</span></span>  
 <span data-ttu-id="7bc53-209">`/parameters` スイッチを使用すると、各種のオプションを設定する単一の XML ファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-209">By using the `/parameters` switch, you can specify a single XML file that sets various options.</span></span> <span data-ttu-id="7bc53-210">設定できるオプションは、XSD.exe ツールの使用方法によって異なります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-210">The options you can set depend on how you are using the XSD.exe tool.</span></span> <span data-ttu-id="7bc53-211">選択肢には、スキーマの生成、コード ファイルの生成、または `DataSet` 機能を含むコード ファイルの生成があります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-211">Choices include generating schemas, generating code files, or generating code files that include `DataSet` features.</span></span> <span data-ttu-id="7bc53-212">たとえば、コード ファイルではなくスキーマを生成する場合、実行可能ファイル (.exe) またはタイプ ライブラリ (.dll) ファイルの名前に `<assembly\>` 要素を設定できます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-212">For example, you can set the `<assembly\>` element to the name of an executable (.exe) or type library (.dll) file when generating a schema, but not when generating a code file.</span></span> <span data-ttu-id="7bc53-213">次の XML に、指定された実行可能ファイルで `<generateSchemas\>` 要素を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-213">The following XML shows how to use the `<generateSchemas\>` element with a specified executable:</span></span>  
  
```xml  
<!-- This is in a file named GenerateSchemas.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <assembly>ConsoleApplication1.exe</assembly>  
</generateSchemas>  
</xsd>  
```  
  
 <span data-ttu-id="7bc53-214">この XML が GenerateSchemas.xml というファイルに含まれる場合、コマンド プロンプトで、`/parameters` スイッチを使用して次のように入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-214">If the preceding XML is contained in a file named GenerateSchemas.xml, then use the `/parameters` switch by typing the following at a command prompt and pressing ENTER:</span></span>  
  
 `xsd /p:GenerateSchemas.xml`  
  
 <span data-ttu-id="7bc53-215">アセンブリにある単一の型のスキーマを生成する場合は、次のような XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-215">On the other hand, if you are generating a schema for a single type found in the assembly, you can use the following XML:</span></span>  
  
```xml  
<!-- This is in a file named GenerateSchemaFromType.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <type>IDItems</type>  
</generateSchemas>  
</xsd>  
```  
  
 <span data-ttu-id="7bc53-216">しかし、上のコードを使用するには、コマンド プロンプトでアセンブリの名前も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-216">But to use preceding code, you must also supply the name of the assembly at the command prompt.</span></span> <span data-ttu-id="7bc53-217">コマンド プロンプトで次のように入力します (XML ファイルの名前を GenerateSchemaFromType.xml と仮定します)。</span><span class="sxs-lookup"><span data-stu-id="7bc53-217">Type the following at a command prompt (presuming the XML file is named GenerateSchemaFromType.xml):</span></span>  
  
 `xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe`  
  
 <span data-ttu-id="7bc53-218">`\<generateSchemas>` 要素に対しては、次のオプションのうち 1 つだけを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-218">You must specify only one of the following options for the `\<generateSchemas>` element.</span></span>  
  
|<span data-ttu-id="7bc53-219">要素</span><span class="sxs-lookup"><span data-stu-id="7bc53-219">Element</span></span>|<span data-ttu-id="7bc53-220">説明</span><span class="sxs-lookup"><span data-stu-id="7bc53-220">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7bc53-221">\<assembly></span><span class="sxs-lookup"><span data-stu-id="7bc53-221">\<assembly></span></span>|<span data-ttu-id="7bc53-222">スキーマを生成するアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-222">Specifies an assembly to generate the schema from.</span></span>|  
|<span data-ttu-id="7bc53-223">\<type></span><span class="sxs-lookup"><span data-stu-id="7bc53-223">\<type></span></span>|<span data-ttu-id="7bc53-224">スキーマを生成するアセンブリに含まれる型を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-224">Specifies a type found in an assembly to generate a schema for.</span></span>|  
|<span data-ttu-id="7bc53-225">\<xml></span><span class="sxs-lookup"><span data-stu-id="7bc53-225">\<xml></span></span>|<span data-ttu-id="7bc53-226">スキーマを生成する XML ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-226">Specifies an XML file to generate a schema for.</span></span>|  
|<span data-ttu-id="7bc53-227">\<xdr></span><span class="sxs-lookup"><span data-stu-id="7bc53-227">\<xdr></span></span>|<span data-ttu-id="7bc53-228">スキーマを生成する XDR ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-228">Specifies an XDR file to generate a schema for.</span></span>|  
  
 <span data-ttu-id="7bc53-229">コード ファイルを生成するには、`<generateClasses\>` 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-229">To generate a code file, use the `<generateClasses\>` element.</span></span> <span data-ttu-id="7bc53-230">コード ファイルを生成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-230">The following example generates a code file.</span></span> <span data-ttu-id="7bc53-231">この例では、生成されるファイルのプログラミング言語と名前空間を設定するための 2 つの属性も示されています。</span><span class="sxs-lookup"><span data-stu-id="7bc53-231">Note that two attributes are also shown that allow you to set the programming language and namespace of the generated file.</span></span>  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>  
</xsd>  
<!-- You must supply an .xsd file when typing in the command line.-->  
<!-- For example: xsd /p:genClasses mySchema.xsd -->  
```  
  
 <span data-ttu-id="7bc53-232">`\<generateClasses>` 要素に設定できるオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7bc53-232">Options you can set for the `\<generateClasses>` element include the following.</span></span>  
  
|<span data-ttu-id="7bc53-233">要素</span><span class="sxs-lookup"><span data-stu-id="7bc53-233">Element</span></span>|<span data-ttu-id="7bc53-234">説明</span><span class="sxs-lookup"><span data-stu-id="7bc53-234">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7bc53-235">\<element></span><span class="sxs-lookup"><span data-stu-id="7bc53-235">\<element></span></span>|<span data-ttu-id="7bc53-236">コードを生成する対象となる .xsd ファイルの要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-236">Specifies an element in the .xsd file to generate code for.</span></span>|  
|<span data-ttu-id="7bc53-237">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="7bc53-237">\<schemaImporterExtensions></span></span>|<span data-ttu-id="7bc53-238"><xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> クラスから派生する型を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-238">Specifies a type derived from the <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> class.</span></span>|  
|<span data-ttu-id="7bc53-239">\<schema></span><span class="sxs-lookup"><span data-stu-id="7bc53-239">\<schema></span></span>|<span data-ttu-id="7bc53-240">コードを生成する XML スキーマ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-240">Specifies a XML Schema file to generate code for.</span></span>  <span data-ttu-id="7bc53-241">複数の \<schema> 要素を使用して、複数の XML スキーマ ファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-241">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|  
  
 <span data-ttu-id="7bc53-242">次の表に、`<generateClasses\>` 要素と共に使用するその他の属性を示します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-242">The following table shows the attributes that can also be used with the `<generateClasses\>` element.</span></span>  
  
|<span data-ttu-id="7bc53-243">属性</span><span class="sxs-lookup"><span data-stu-id="7bc53-243">Attribute</span></span>|<span data-ttu-id="7bc53-244">説明</span><span class="sxs-lookup"><span data-stu-id="7bc53-244">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7bc53-245">language</span><span class="sxs-lookup"><span data-stu-id="7bc53-245">language</span></span>|<span data-ttu-id="7bc53-246">使用するプログラミング言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-246">Specifies the programming language to use.</span></span> <span data-ttu-id="7bc53-247">`CS` (C#、既定値)、`VB` (Visual Basic)、`JS` (JScript)、または `VJS` (Visual J#) から選択します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-247">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="7bc53-248"><xref:System.CodeDom.Compiler.CodeDomProvider> を実装するクラスの完全修飾名を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-248">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|  
|<span data-ttu-id="7bc53-249">namespace</span><span class="sxs-lookup"><span data-stu-id="7bc53-249">namespace</span></span>|<span data-ttu-id="7bc53-250">生成するコードの名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-250">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="7bc53-251">名前空間は、スペースやバックスラッシュ文字を使用しないなどの CLR 標準に準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-251">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|  
|<span data-ttu-id="7bc53-252">オプション</span><span class="sxs-lookup"><span data-stu-id="7bc53-252">options</span></span>|<span data-ttu-id="7bc53-253">`none`、`properties` (パブリック フィールドの代わりにプロパティを生成)、`order`、または `enableDataBinding` (前の「XSD ファイルのオプション」セクションの `/order` と `/enableDataBinding` スイッチを参照) のいずれかの値です。</span><span class="sxs-lookup"><span data-stu-id="7bc53-253">One of the following values: `none`, `properties` (generates properties instead of public fields), `order`, or `enableDataBinding` (see the `/order` and `/enableDataBinding` switches in the preceding XSD File Options section.</span></span>|  
  
 <span data-ttu-id="7bc53-254">`DataSet` 要素を使用すると、`<generateDataSets\>` コードを生成する方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-254">You can also control how `DataSet` code is generated by using the `<generateDataSets\>` element.</span></span> <span data-ttu-id="7bc53-255">次の XML は、生成されたコードが `DataSet` 構造体 (<xref:System.Data.DataTable> クラスなど) を使用して指定された要素のための Visual Basic コードを作成するように指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-255">The following XML specifies that the generated codeuses `DataSet` structures (such as the <xref:System.Data.DataTable> class) to create Visual Basic code for a specified element.</span></span> <span data-ttu-id="7bc53-256">生成された DataSet 構造体では LINQ クエリがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-256">The generated DataSet structures will support LINQ queries.</span></span>  
  
 `<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>`  
  
 `<generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>`  
  
 `</generateDataSet>`  
  
 `</xsd>`  
  
 <span data-ttu-id="7bc53-257">`<generateDataSet\>` 要素に設定できるオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7bc53-257">Options you can set for the `<generateDataSet\>` element include the following.</span></span>  
  
|<span data-ttu-id="7bc53-258">要素</span><span class="sxs-lookup"><span data-stu-id="7bc53-258">Element</span></span>|<span data-ttu-id="7bc53-259">説明</span><span class="sxs-lookup"><span data-stu-id="7bc53-259">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7bc53-260">\<schema></span><span class="sxs-lookup"><span data-stu-id="7bc53-260">\<schema></span></span>|<span data-ttu-id="7bc53-261">コードを生成する XML スキーマ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-261">Specifies an XML Schema file to generate code for.</span></span> <span data-ttu-id="7bc53-262">複数の \<schema> 要素を使用して、複数の XML スキーマ ファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-262">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|  
  
 <span data-ttu-id="7bc53-263">`<generateDataSet\>` 要素と共に使用できる属性を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-263">The following table shows the attributes that can be used with the `<generateDataSet\>` element.</span></span>  
  
|<span data-ttu-id="7bc53-264">属性</span><span class="sxs-lookup"><span data-stu-id="7bc53-264">Attribute</span></span>|<span data-ttu-id="7bc53-265">説明</span><span class="sxs-lookup"><span data-stu-id="7bc53-265">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7bc53-266">enableLinqDataSet</span><span class="sxs-lookup"><span data-stu-id="7bc53-266">enableLinqDataSet</span></span>|<span data-ttu-id="7bc53-267">LINQ to DataSet を使用して、生成された DataSet を照会できるように指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-267">Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="7bc53-268">既定値は false です。</span><span class="sxs-lookup"><span data-stu-id="7bc53-268">The default value is false.</span></span>|  
|<span data-ttu-id="7bc53-269">language</span><span class="sxs-lookup"><span data-stu-id="7bc53-269">language</span></span>|<span data-ttu-id="7bc53-270">使用するプログラミング言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-270">Specifies the programming language to use.</span></span> <span data-ttu-id="7bc53-271">`CS` (C#、既定値)、`VB` (Visual Basic)、`JS` (JScript)、または `VJS` (Visual J#) から選択します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-271">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="7bc53-272"><xref:System.CodeDom.Compiler.CodeDomProvider> を実装するクラスの完全修飾名を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-272">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|  
|<span data-ttu-id="7bc53-273">namespace</span><span class="sxs-lookup"><span data-stu-id="7bc53-273">namespace</span></span>|<span data-ttu-id="7bc53-274">生成するコードの名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-274">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="7bc53-275">名前空間は、スペースやバックスラッシュ文字を使用しないなどの CLR 標準に準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-275">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|  
  
 <span data-ttu-id="7bc53-276">トップ レベルの `<xsd\>` 要素に設定できる属性があります。</span><span class="sxs-lookup"><span data-stu-id="7bc53-276">There are attributes that you can set on the top level `<xsd\>` element.</span></span> <span data-ttu-id="7bc53-277">これらのオプションは、`<generateSchemas\>`、`<generateClasses\>`、または `<generateDataSet\>` の各子要素と共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="7bc53-277">These options can be used with any of the child elements (`<generateSchemas\>`, `<generateClasses\>` or `<generateDataSet\>`).</span></span> <span data-ttu-id="7bc53-278">次の XML コードは、"MyOutputDirectory" という出力ディレクトリの "IDItems" という要素のコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-278">The following XML code generates code for an element named "IDItems" in the output directory named "MyOutputDirectory".</span></span>  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>  
<generateClasses>  
<element>IDItems</element>  
</generateClasses>  
</xsd>  
```  
  
 <span data-ttu-id="7bc53-279">次の表に、`\<xsd>` 要素と共に使用するその他の属性を示します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-279">The following table shows the attributes that can also be used with the `\<xsd>` element.</span></span>  
  
|<span data-ttu-id="7bc53-280">属性</span><span class="sxs-lookup"><span data-stu-id="7bc53-280">Attribute</span></span>|<span data-ttu-id="7bc53-281">説明</span><span class="sxs-lookup"><span data-stu-id="7bc53-281">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7bc53-282">出力</span><span class="sxs-lookup"><span data-stu-id="7bc53-282">output</span></span>|<span data-ttu-id="7bc53-283">生成されたスキーマまたはコード ファイルが格納されるディレクトリの名前です。</span><span class="sxs-lookup"><span data-stu-id="7bc53-283">The name of a directory where the generated schema or code file will be placed.</span></span>|  
|<span data-ttu-id="7bc53-284">nologo</span><span class="sxs-lookup"><span data-stu-id="7bc53-284">nologo</span></span>|<span data-ttu-id="7bc53-285">バナーを表示しません。</span><span class="sxs-lookup"><span data-stu-id="7bc53-285">Suppresses the banner.</span></span> <span data-ttu-id="7bc53-286">`true` または `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-286">Set to `true` or `false`.</span></span>|  
|<span data-ttu-id="7bc53-287">ヘルプ</span><span class="sxs-lookup"><span data-stu-id="7bc53-287">help</span></span>|<span data-ttu-id="7bc53-288">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-288">Displays command syntax and options for the tool.</span></span> <span data-ttu-id="7bc53-289">`true` または `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-289">Set to `true` or `false`.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="7bc53-290">例</span><span class="sxs-lookup"><span data-stu-id="7bc53-290">Examples</span></span>  
 <span data-ttu-id="7bc53-291">`myFile.xdr` から XML スキーマを生成し、現在のディレクトリに保存するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-291">The following command generates an XML schema from `myFile.xdr` and saves it to the current directory.</span></span>  
  
```  
xsd myFile.xdr   
```  
  
 <span data-ttu-id="7bc53-292">`myFile.xml` から XML スキーマを生成し、指定したディレクトリに保存するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-292">The following command generates an XML schema from `myFile.xml` and saves it to the specified directory.</span></span>  
  
```  
xsd myFile.xml /outputdir:myOutputDir  
```  
  
 <span data-ttu-id="7bc53-293">指定したスキーマと対応するデータセットを C# 言語で生成し、現在のディレクトリ内に `XSDSchemaFile.cs` として保存するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-293">The following command generates a data set that corresponds to the specified schema in the C# language and saves it as `XSDSchemaFile.cs` in the current directory.</span></span>  
  
```  
xsd /dataset /language:CS XSDSchemaFile.xsd  
```  
  
 <span data-ttu-id="7bc53-294">`myAssembly.dll` アセンブリ内のすべての型について XML スキーマを生成し、それらを `schema0.xsd` として現在のディレクトリ内に保存するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7bc53-294">The following command generates XML schemas for all types in the assembly `myAssembly.dll` and saves them as `schema0.xsd` in the current directory.</span></span>  
  
```  
xsd myAssembly.dll    
```  
  
## <a name="see-also"></a><span data-ttu-id="7bc53-295">参照</span><span class="sxs-lookup"><span data-stu-id="7bc53-295">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>  
 <span data-ttu-id="7bc53-296">[ツール](../../../docs/framework/tools/index.md)    </span><span class="sxs-lookup"><span data-stu-id="7bc53-296">[Tools](../../../docs/framework/tools/index.md)    </span></span>  
 [<span data-ttu-id="7bc53-297">Visual Studio 用開発者コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="7bc53-297">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)  
 [<span data-ttu-id="7bc53-298">LINQ to DataSet の概要</span><span class="sxs-lookup"><span data-stu-id="7bc53-298">LINQ to DataSet Overview</span></span>](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [<span data-ttu-id="7bc53-299">型指定された DataSet のクエリ</span><span class="sxs-lookup"><span data-stu-id="7bc53-299">Querying Typed DataSets</span></span>](../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [<span data-ttu-id="7bc53-300">統合言語クエリ (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7bc53-300">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
