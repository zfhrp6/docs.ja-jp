---
title: "XML シリアライザー ジェネレーター ツール (Sgen.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0e2f268dc2ab1e2aebe2f51d733a59bd093329d5
ms.sourcegitcommit: bf8a3ba647252010bdce86dd914ac6c61b5ba89d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2018
---
# <a name="xml-serializer-generator-tool-sgenexe"></a><span data-ttu-id="9876c-102">XML シリアライザー ジェネレーター ツール (Sgen.exe)</span><span class="sxs-lookup"><span data-stu-id="9876c-102">XML Serializer Generator Tool (Sgen.exe)</span></span>
<span data-ttu-id="9876c-103">XML シリアライザー ジェネレーターは、指定された型のオブジェクトをシリアル化または逆シリアル化するとき、<xref:System.Xml.Serialization.XmlSerializer> の起動パフォーマンスを向上させるために、指定されたアセンブリの型に対して XML シリアル化アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="9876c-103">The XML Serializer Generator creates an XML serialization assembly for types in a specified assembly in order to improve the startup performance of a <xref:System.Xml.Serialization.XmlSerializer> when it serializes or deserializes objects of the specified types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9876c-104">構文</span><span class="sxs-lookup"><span data-stu-id="9876c-104">Syntax</span></span>  
  
```  
sgen [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9876c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9876c-105">Parameters</span></span>  
  
|<span data-ttu-id="9876c-106">オプション</span><span class="sxs-lookup"><span data-stu-id="9876c-106">Option</span></span>|<span data-ttu-id="9876c-107">説明</span><span class="sxs-lookup"><span data-stu-id="9876c-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9876c-108">**/a****[ssembly]****:***filename*</span><span class="sxs-lookup"><span data-stu-id="9876c-108">**/a**[**ssembly**]**:***filename*</span></span>|<span data-ttu-id="9876c-109">アセンブリ、または *filename* によって指定される実行可能ファイルに含まれるすべての型に対して、シリアル化コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="9876c-109">Generates serialization code for all the types contained in the assembly or executable specified by *filename*.</span></span> <span data-ttu-id="9876c-110">指定できるファイル名は 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="9876c-110">Only one file name can be provided.</span></span> <span data-ttu-id="9876c-111">この引数を複数指定した場合は、最後のファイル名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9876c-111">If this argument is repeated, the last file name is used.</span></span>|  
|<span data-ttu-id="9876c-112">**/c[ompiler]:** *options*</span><span class="sxs-lookup"><span data-stu-id="9876c-112">**/c[ompiler]:** *options*</span></span>|<span data-ttu-id="9876c-113">オプションを C# コンパイラに渡すように指定します。</span><span class="sxs-lookup"><span data-stu-id="9876c-113">Specifies the options to pass to the C# compiler.</span></span> <span data-ttu-id="9876c-114">csc.exe のすべてのオプションがサポートされ、コンパイラに渡されます。</span><span class="sxs-lookup"><span data-stu-id="9876c-114">All csc.exe options are supported as they are passed to the compiler.</span></span> <span data-ttu-id="9876c-115">このオプションを使用して、アセンブリに署名してキー ファイルを指定するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="9876c-115">This can be used to specify that the assembly should be signed and to specify the key file.</span></span>|  
|<span data-ttu-id="9876c-116">**/d****[ebug]**</span><span class="sxs-lookup"><span data-stu-id="9876c-116">**/d**[**ebug**]</span></span>|<span data-ttu-id="9876c-117">デバッガーで使用できるイメージを生成します。</span><span class="sxs-lookup"><span data-stu-id="9876c-117">Generates an image that can be used with a debugger.</span></span>|  
|<span data-ttu-id="9876c-118">**/f[orce]**</span><span class="sxs-lookup"><span data-stu-id="9876c-118">**/f[orce]**</span></span>|<span data-ttu-id="9876c-119">同じ名前の既存のアセンブリに上書きします。</span><span class="sxs-lookup"><span data-stu-id="9876c-119">Forces the overwriting of an existing assembly of the same name.</span></span> <span data-ttu-id="9876c-120">既定値は **false** です。</span><span class="sxs-lookup"><span data-stu-id="9876c-120">The default is **false**.</span></span>|  
|<span data-ttu-id="9876c-121">**/help または /?**</span><span class="sxs-lookup"><span data-stu-id="9876c-121">**/help or /?**</span></span>|<span data-ttu-id="9876c-122">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="9876c-122">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="9876c-123">**/k****[eep]**</span><span class="sxs-lookup"><span data-stu-id="9876c-123">**/k**[**eep**]</span></span>|<span data-ttu-id="9876c-124">生成されたソース ファイルとその他の一時ファイルをシリアル化アセンブリにコンパイルした後、元のファイルを削除しません。</span><span class="sxs-lookup"><span data-stu-id="9876c-124">Suppresses the deletion of the generated source files and other temporary files after they have been compiled into the serialization assembly.</span></span> <span data-ttu-id="9876c-125">このオプションを使用して、ツールが特定の型に対してシリアル化コードを生成するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9876c-125">This can be used to determine whether the tool is generating serialization code for a particular type.</span></span>|  
|<span data-ttu-id="9876c-126">**/n****[ologo]**</span><span class="sxs-lookup"><span data-stu-id="9876c-126">**/n**[**ologo**]</span></span>|<span data-ttu-id="9876c-127">Microsoft の著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="9876c-127">Suppresses the display of the Microsoft startup banner.</span></span>|  
|<span data-ttu-id="9876c-128">**/o****[ut]****:***path*</span><span class="sxs-lookup"><span data-stu-id="9876c-128">**/o**[**ut**]**:***path*</span></span>|<span data-ttu-id="9876c-129">生成されたアセンブリの保存先のディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="9876c-129">Specifies the directory in which to save the generated assembly.</span></span> <span data-ttu-id="9876c-130">**注:** 生成されたアセンブリの名前は、入力アセンブリの名前と "xmlSerializers.dll" で構成されます。</span><span class="sxs-lookup"><span data-stu-id="9876c-130">**Note:**  The name of the generated assembly is composed of the name of the input assembly plus "xmlSerializers.dll".</span></span>|  
|<span data-ttu-id="9876c-131">**/p****[roxytypes]**</span><span class="sxs-lookup"><span data-stu-id="9876c-131">**/p**[**roxytypes**]</span></span>|<span data-ttu-id="9876c-132">XML Web サービス プロキシ型に対してのみシリアル化コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="9876c-132">Generates serialization code only for the XML Web service proxy types.</span></span>|  
|<span data-ttu-id="9876c-133">**/r****[eference]****:***assemblyfiles*</span><span class="sxs-lookup"><span data-stu-id="9876c-133">**/r**[**eference**]**:***assemblyfiles*</span></span>|<span data-ttu-id="9876c-134">XML シリアル化が必要な型によって参照されるアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="9876c-134">Specifies the assemblies that are referenced by the types requiring XML serialization.</span></span> <span data-ttu-id="9876c-135">コンマで区切られた複数のアセンブリ ファイルを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="9876c-135">Accepts multiple assembly files separated by commas.</span></span>|  
|<span data-ttu-id="9876c-136">**/s****[ilent]**</span><span class="sxs-lookup"><span data-stu-id="9876c-136">**/s**[**ilent**]</span></span>|<span data-ttu-id="9876c-137">成功メッセージを表示しません。</span><span class="sxs-lookup"><span data-stu-id="9876c-137">Suppresses the display of success messages.</span></span>|  
|<span data-ttu-id="9876c-138">**/t****[ype]****:***type*</span><span class="sxs-lookup"><span data-stu-id="9876c-138">**/t**[**ype**]**:***type*</span></span>|<span data-ttu-id="9876c-139">指定された型に対してのみ、シリアル化コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="9876c-139">Generates serialization code only for the specified type.</span></span>|  
|<span data-ttu-id="9876c-140">**/v****[erbose]**</span><span class="sxs-lookup"><span data-stu-id="9876c-140">**/v**[**erbose**]</span></span>|<span data-ttu-id="9876c-141">デバッグに関する詳細出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="9876c-141">Displays verbose output for debugging.</span></span> <span data-ttu-id="9876c-142"><xref:System.Xml.Serialization.XmlSerializer> でシリアル化できない対象アセンブリの型を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9876c-142">Lists types from the target assembly that cannot be serialized with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|<span data-ttu-id="9876c-143">**/?**</span><span class="sxs-lookup"><span data-stu-id="9876c-143">**/?**</span></span>|<span data-ttu-id="9876c-144">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="9876c-144">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9876c-145">コメント</span><span class="sxs-lookup"><span data-stu-id="9876c-145">Remarks</span></span>  
 <span data-ttu-id="9876c-146">XML シリアライザー ジェネレーターを使用しない場合、<xref:System.Xml.Serialization.XmlSerializer> はアプリケーションを実行するたびに、各型に対してシリアル化コードとシリアル化アセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="9876c-146">When the XML Serializer Generator is not used, a <xref:System.Xml.Serialization.XmlSerializer> generates serialization code and a serialization assembly for each type every time an application is run.</span></span> <span data-ttu-id="9876c-147">XML シリアル化の起動時のパフォーマンスを向上させるには、事前にそれらのアセンブリを生成するのに Sgen.exe ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="9876c-147">To improve the performance of XML serialization startup, use the Sgen.exe tool to generate those assemblies in advance.</span></span> <span data-ttu-id="9876c-148">生成したアセンブリは、アプリケーションで配置できます。</span><span class="sxs-lookup"><span data-stu-id="9876c-148">These assemblies can then be deployed with the application.</span></span>  
  
 <span data-ttu-id="9876c-149">XML シリアライザー ジェネレーターは、サーバーとの通信に XML Web サービス プロキシを使用するクライアントのパフォーマンスも向上させますが、これは型が初めて読み込まれるとき、シリアル化プロセスによってパフォーマンスが低下しないためです。</span><span class="sxs-lookup"><span data-stu-id="9876c-149">The XML Serializer Generator can also improve the performance of clients that use XML Web service proxies to communicate with servers because the serialization process will not incur a performance hit when the type is loaded the first time.</span></span>  
  
 <span data-ttu-id="9876c-150">これらの生成されたアセンブリは、Web サービスのサーバー側では使用できません。</span><span class="sxs-lookup"><span data-stu-id="9876c-150">These generated assemblies cannot be used on the server side of a Web service.</span></span> <span data-ttu-id="9876c-151">このツールは、Web サービス クライアントと手動シリアル化シナリオに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9876c-151">This tool is only for Web service clients and manual serialization scenarios.</span></span>  
  
 <span data-ttu-id="9876c-152">シリアル化する型を含むアセンブリの名前が MyType.dll の場合、関連するシリアル化アセンブリの名前は MyType.XmlSerializers.dll となります。</span><span class="sxs-lookup"><span data-stu-id="9876c-152">If the assembly containing the type to serialize is named MyType.dll, then the associated serialization assembly will be named MyType.XmlSerializers.dll.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9876c-153">例</span><span class="sxs-lookup"><span data-stu-id="9876c-153">Examples</span></span>  
 <span data-ttu-id="9876c-154">次のコマンドは、Data.dll という名前のアセンブリに含まれるすべての型をシリアル化するために、Data.XmlSerializers.dll という名前のアセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="9876c-154">The following command creates an assembly named Data.XmlSerializers.dll for serializing all the types contained in the assembly named Data.dll.</span></span>  
  
```  
sgen Data.dll   
```  
  
 <span data-ttu-id="9876c-155">Data.XmlSerializers.dll アセンブリは、Data.dll の型をシリアル化および逆シリアル化する必要のあるコードから参照できます。</span><span class="sxs-lookup"><span data-stu-id="9876c-155">The Data.XmlSerializers.dll assembly can be referenced from code that needs to serialize and deserialize the types in Data.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9876c-156">参照</span><span class="sxs-lookup"><span data-stu-id="9876c-156">See Also</span></span>  
 [<span data-ttu-id="9876c-157">ツール</span><span class="sxs-lookup"><span data-stu-id="9876c-157">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="9876c-158">XML Web サービスの概要</span><span class="sxs-lookup"><span data-stu-id="9876c-158">XML Web Services Overview</span></span>](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d)  
 [<span data-ttu-id="9876c-159">Visual Studio 用開発者コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="9876c-159">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
