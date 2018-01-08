---
title: "SecAnnotate.exe (.NET セキュリティ アノテーター ツール)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e68679464db3875a79d6aa07a6e10240ada13365
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="secannotateexe-net-security-annotator-tool"></a><span data-ttu-id="50e21-102">SecAnnotate.exe (.NET セキュリティ アノテーター ツール)</span><span class="sxs-lookup"><span data-stu-id="50e21-102">SecAnnotate.exe (.NET Security Annotator Tool)</span></span>
<span data-ttu-id="50e21-103">.NET セキュリティ アノテーター ツール (SecAnnotate.exe) は、1 つ以上のアセンブリの `SecurityCritical` 部分と `SecuritySafeCritical` 部分を識別するコマンド ライン アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="50e21-103">The .NET Security Annotator tool (SecAnnotate.exe) is a command-line application that identifies the `SecurityCritical` and `SecuritySafeCritical` portions of one or more assemblies.</span></span>  
  
 <span data-ttu-id="50e21-104">Visual Studio 拡張機能である[セキュリティ アノテーター](http://go.microsoft.com/fwlink/?LinkId=198007)は、SecAnnotate.exe のグラフィカル ユーザー インターフェイスであり、Visual Studio から実行できます。</span><span class="sxs-lookup"><span data-stu-id="50e21-104">A Visual Studio extension, [Security Annotator](http://go.microsoft.com/fwlink/?LinkId=198007), provides a graphical user interface to SecAnnotate.exe and enables you to run the tool from Visual Studio.</span></span>  
  
 <span data-ttu-id="50e21-105">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="50e21-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="50e21-106">このツールを実行するには、開発者コマンド プロンプト (または、Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="50e21-106">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="50e21-107">詳細については、「[Visual Studio 用開発者コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50e21-107">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="50e21-108">コマンド プロンプトで次のコマンドを入力します。*parameters* は、次のセクションで説明するパラメーターで、*assemblies* は、空白で区切られた 1 つ以上のアセンブリ名で構成されます。</span><span class="sxs-lookup"><span data-stu-id="50e21-108">At the command prompt, type the following, where *parameters* are described in the following section, and *assemblies* consist of one or more assembly names separated by blanks:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50e21-109">構文</span><span class="sxs-lookup"><span data-stu-id="50e21-109">Syntax</span></span>  
  
```  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50e21-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50e21-110">Parameters</span></span>  
  
|<span data-ttu-id="50e21-111">オプション</span><span class="sxs-lookup"><span data-stu-id="50e21-111">Option</span></span>|<span data-ttu-id="50e21-112">説明</span><span class="sxs-lookup"><span data-stu-id="50e21-112">Description</span></span>|  
|------------|-----------------|  
|`/a`<br /><br /> <span data-ttu-id="50e21-113">または</span><span class="sxs-lookup"><span data-stu-id="50e21-113">or</span></span><br /><br /> `/showstatistics`|<span data-ttu-id="50e21-114">分析対象のアセンブリにおける透過性の使用に関する統計情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="50e21-114">Shows statistics about the use of transparency in assemblies that are being analyzed.</span></span>|  
|<span data-ttu-id="50e21-115">`/d:` *directory*</span><span class="sxs-lookup"><span data-stu-id="50e21-115">`/d:` *directory*</span></span><br /><br /> <span data-ttu-id="50e21-116">または</span><span class="sxs-lookup"><span data-stu-id="50e21-116">or</span></span><br /><br /> <span data-ttu-id="50e21-117">`/referencedir:` *directory*</span><span class="sxs-lookup"><span data-stu-id="50e21-117">`/referencedir:` *directory*</span></span>|<span data-ttu-id="50e21-118">注釈の処理時に依存アセンブリを検索するディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="50e21-118">Specifies a directory to search for dependent assemblies during annotation.</span></span>|  
|`/i`<br /><br /> <span data-ttu-id="50e21-119">または</span><span class="sxs-lookup"><span data-stu-id="50e21-119">or</span></span><br /><br /> `/includesignatures`|<span data-ttu-id="50e21-120">署名に関する拡張情報を注釈レポート ファイルに含めます。</span><span class="sxs-lookup"><span data-stu-id="50e21-120">Includes extended signature information in the annotation report file.</span></span>|  
|`/n`<br /><br /> <span data-ttu-id="50e21-121">または</span><span class="sxs-lookup"><span data-stu-id="50e21-121">or</span></span><br /><br /> `/nogac`|<span data-ttu-id="50e21-122">グローバル アセンブリ キャッシュ内の参照アセンブリを検索しないようにします。</span><span class="sxs-lookup"><span data-stu-id="50e21-122">Suppresses searching for referenced assemblies in the global assembly cache.</span></span>|  
|<span data-ttu-id="50e21-123">`/o:` *output.xml*</span><span class="sxs-lookup"><span data-stu-id="50e21-123">`/o:` *output.xml*</span></span><br /><br /> <span data-ttu-id="50e21-124">または</span><span class="sxs-lookup"><span data-stu-id="50e21-124">or</span></span><br /><br /> <span data-ttu-id="50e21-125">`/out:` *output.xml*</span><span class="sxs-lookup"><span data-stu-id="50e21-125">`/out:` *output.xml*</span></span>|<span data-ttu-id="50e21-126">出力注釈ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="50e21-126">Specifies the output annotation file.</span></span>|  
|<span data-ttu-id="50e21-127">`/p:` *maxpasses*</span><span class="sxs-lookup"><span data-stu-id="50e21-127">`/p:` *maxpasses*</span></span><br /><br /> <span data-ttu-id="50e21-128">または</span><span class="sxs-lookup"><span data-stu-id="50e21-128">or</span></span><br /><br /> <span data-ttu-id="50e21-129">`/maximumpasses:` *maxpasses*</span><span class="sxs-lookup"><span data-stu-id="50e21-129">`/maximumpasses:` *maxpasses*</span></span>|<span data-ttu-id="50e21-130">新しい注釈の生成を停止するまでにアセンブリで実行する注釈パスの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="50e21-130">Specifies the maximum number of annotation passes to make on assemblies before stopping the generation of new annotations.</span></span>|  
|`/q`<br /><br /> <span data-ttu-id="50e21-131">または</span><span class="sxs-lookup"><span data-stu-id="50e21-131">or</span></span><br /><br /> `/quiet`|<span data-ttu-id="50e21-132">クワイエット モードを指定します。このモードでは、ステータス メッセージは出力されず、エラー情報だけが出力されます。</span><span class="sxs-lookup"><span data-stu-id="50e21-132">Specifies quiet mode, in which the annotator does not output status messages; it outputs only error information.</span></span>|  
|<span data-ttu-id="50e21-133">`/r:` *assembly*</span><span class="sxs-lookup"><span data-stu-id="50e21-133">`/r:` *assembly*</span></span><br /><br /> <span data-ttu-id="50e21-134">または</span><span class="sxs-lookup"><span data-stu-id="50e21-134">or</span></span><br /><br /> <span data-ttu-id="50e21-135">`/referenceassembly:` *assembly*</span><span class="sxs-lookup"><span data-stu-id="50e21-135">`/referenceassembly:` *assembly*</span></span>|<span data-ttu-id="50e21-136">注釈の処理時、依存アセンブリを解決するときに、指定したアセンブリを含めます。</span><span class="sxs-lookup"><span data-stu-id="50e21-136">Includes the specified assembly when resolving dependent assemblies during annotation.</span></span> <span data-ttu-id="50e21-137">参照アセンブリは参照パスにあるアセンブリよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="50e21-137">Reference assemblies are given priority over assemblies that are found in the reference path.</span></span>|  
|<span data-ttu-id="50e21-138">`/s:` *rulename*</span><span class="sxs-lookup"><span data-stu-id="50e21-138">`/s:` *rulename*</span></span><br /><br /> <span data-ttu-id="50e21-139">または</span><span class="sxs-lookup"><span data-stu-id="50e21-139">or</span></span><br /><br /> <span data-ttu-id="50e21-140">`/suppressrule:` *rulename*</span><span class="sxs-lookup"><span data-stu-id="50e21-140">`/suppressrule:` *rulename*</span></span>|<span data-ttu-id="50e21-141">入力アセンブリについて、指定した透過性規則を実行しないようにします。</span><span class="sxs-lookup"><span data-stu-id="50e21-141">Suppresses running the specified transparency rule on the input assemblies.</span></span>|  
|`/t`<br /><br /> <span data-ttu-id="50e21-142">または</span><span class="sxs-lookup"><span data-stu-id="50e21-142">or</span></span><br /><br /> `/forcetransparent`|<span data-ttu-id="50e21-143">強制的に、透過性注釈がないすべてのアセンブリを完全に透過的として扱います。</span><span class="sxs-lookup"><span data-stu-id="50e21-143">Forces the Annotator tool to treat all assemblies that do not have any transparency annotations as if they were entirely transparent.</span></span>|  
|<span data-ttu-id="50e21-144">`/t`:*assembly*</span><span class="sxs-lookup"><span data-stu-id="50e21-144">`/t`:*assembly*</span></span><br /><br /> <span data-ttu-id="50e21-145">または</span><span class="sxs-lookup"><span data-stu-id="50e21-145">or</span></span><br /><br /> <span data-ttu-id="50e21-146">`/forcetransparent`:*assembly*</span><span class="sxs-lookup"><span data-stu-id="50e21-146">`/forcetransparent`:*assembly*</span></span>|<span data-ttu-id="50e21-147">現在のアセンブリ レベルの注釈に関係なく、指定されたアセンブリを強制的に透過的にします。</span><span class="sxs-lookup"><span data-stu-id="50e21-147">Force the given assembly to be transparent, regardless of its current assembly-level annotations.</span></span>|  
|||  
|`/v`<br /><br /> <span data-ttu-id="50e21-148">または</span><span class="sxs-lookup"><span data-stu-id="50e21-148">or</span></span><br /><br /> `/verify`|<span data-ttu-id="50e21-149">アセンブリの注釈が正しいことだけを検証します。アセンブリで検証されない場合に、必要な注釈をすべて見つけるために複数のパスを実行しようとはしません。</span><span class="sxs-lookup"><span data-stu-id="50e21-149">Verifies only that an assembly's annotations are correct; does not attempt to make multiple passes to find all required annotations if the assembly does not verify.</span></span>|  
|`/x`<br /><br /> <span data-ttu-id="50e21-150">または</span><span class="sxs-lookup"><span data-stu-id="50e21-150">or</span></span><br /><br /> `/verbose`|<span data-ttu-id="50e21-151">注釈の処理時に詳細を出力することを指定します。</span><span class="sxs-lookup"><span data-stu-id="50e21-151">Specifies verbose output while annotating.</span></span>|  
|<span data-ttu-id="50e21-152">`/y:` *directory*</span><span class="sxs-lookup"><span data-stu-id="50e21-152">`/y:` *directory*</span></span><br /><br /> <span data-ttu-id="50e21-153">または</span><span class="sxs-lookup"><span data-stu-id="50e21-153">or</span></span><br /><br /> <span data-ttu-id="50e21-154">`/symbolpath:` *directory*</span><span class="sxs-lookup"><span data-stu-id="50e21-154">`/symbolpath:` *directory*</span></span>|<span data-ttu-id="50e21-155">注釈の処理時、シンボル ファイルを検索するときに、指定したディレクトリを含めます。</span><span class="sxs-lookup"><span data-stu-id="50e21-155">Includes the specified directory when searching for symbol files during annotation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50e21-156">コメント</span><span class="sxs-lookup"><span data-stu-id="50e21-156">Remarks</span></span>  
 <span data-ttu-id="50e21-157">パラメーターとアセンブリは、コマンド ラインでアット マーク (@) をプレフィックスとして付けて指定する応答ファイルで指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="50e21-157">Parameters and assemblies may also be provided in a response file that is specified on the command line and prefixed with an at sign (@).</span></span> <span data-ttu-id="50e21-158">応答ファイルの各行には、1 つのパラメーターまたはアセンブリの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50e21-158">Each line in the response file should contain a single parameter or assembly name.</span></span>  
  
 <span data-ttu-id="50e21-159">.NET セキュリティ アノテーターについて詳しくは、.NET セキュリティ ブログの「[Using SecAnnotate to Analyze Your Assemblies for Transparency Violations](http://go.microsoft.com/fwlink/?LinkId=187648)」(SecAnnotate を使用したアセンブリでの透過性違反の分析) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="50e21-159">For more information about the .NET Security Annotator, see the entry [Using SecAnnotate to Analyze Your Assemblies for Transparency Violations](http://go.microsoft.com/fwlink/?LinkId=187648) in the .NET Security blog.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="50e21-160">使用例</span><span class="sxs-lookup"><span data-stu-id="50e21-160">Examples</span></span>
