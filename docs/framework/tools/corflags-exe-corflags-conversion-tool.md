---
title: "CorFlags.exe (CorFlags 変換ツール)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 111c697d4d62cd52cd7913039e3c17e8a25ab50d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="d0294-102">CorFlags.exe (CorFlags 変換ツール)</span><span class="sxs-lookup"><span data-stu-id="d0294-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="d0294-103">CorFlags 変換ツールを使用して、ポータブル実行可能 (PE) ファイル イメージのヘッダー内の CorFlags セクションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="d0294-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="d0294-104">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="d0294-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="d0294-105">このツールを実行するには、開発者コマンド プロンプト (または、Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="d0294-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="d0294-106">詳細については、「[Visual Studio 用開発者コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0294-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="d0294-107">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="d0294-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0294-108">構文</span><span class="sxs-lookup"><span data-stu-id="d0294-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0294-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d0294-109">Parameters</span></span>  
  
|<span data-ttu-id="d0294-110">必須パラメーター</span><span class="sxs-lookup"><span data-stu-id="d0294-110">Required parameter</span></span>|<span data-ttu-id="d0294-111">説明</span><span class="sxs-lookup"><span data-stu-id="d0294-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="d0294-112">CorFlags を設定するアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="d0294-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="d0294-113">オプション</span><span class="sxs-lookup"><span data-stu-id="d0294-113">Option</span></span>|<span data-ttu-id="d0294-114">説明</span><span class="sxs-lookup"><span data-stu-id="d0294-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d0294-115">**32BIT[REQ]+**</span><span class="sxs-lookup"><span data-stu-id="d0294-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="d0294-116">32BITREQUIRED フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="d0294-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="d0294-117">**/32BIT[REQ]-**</span><span class="sxs-lookup"><span data-stu-id="d0294-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="d0294-118">32BITREQUIRED フラグをクリアします。</span><span class="sxs-lookup"><span data-stu-id="d0294-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="d0294-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="d0294-119">**/32BITPREF+**</span></span>|<span data-ttu-id="d0294-120">32BITPREFERRED フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="d0294-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="d0294-121">アプリは、64 ビット プラットフォーム上でも 32 ビット プロセスとして実行します。</span><span class="sxs-lookup"><span data-stu-id="d0294-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="d0294-122">このフラグは、EXE ファイルでのみ設定します。</span><span class="sxs-lookup"><span data-stu-id="d0294-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="d0294-123">このフラグを DLL で設定した場合、64 ビット プロセスで DLL を読み込むことができず、<xref:System.BadImageFormatException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d0294-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="d0294-124">このフラグを設定した EXE ファイルは、64 ビット プロセスで読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="d0294-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="d0294-125">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] の新機能。</span><span class="sxs-lookup"><span data-stu-id="d0294-125">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="d0294-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="d0294-126">**/32BITPREF-**</span></span>|<span data-ttu-id="d0294-127">32BITPREFERRED フラグをクリアします。</span><span class="sxs-lookup"><span data-stu-id="d0294-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="d0294-128">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] の新機能。</span><span class="sxs-lookup"><span data-stu-id="d0294-128">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="d0294-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="d0294-129">**/?**</span></span>|<span data-ttu-id="d0294-130">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="d0294-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="d0294-131">**/Force**</span><span class="sxs-lookup"><span data-stu-id="d0294-131">**/Force**</span></span>|<span data-ttu-id="d0294-132">厳密な名前が付けられているアセンブリであっても、強制的に更新します。</span><span class="sxs-lookup"><span data-stu-id="d0294-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="d0294-133">**重要:**  厳密な名前が付けられているアセンブリを更新する場合は、そのコードを実行する前に再署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0294-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="d0294-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="d0294-134">**/help**</span></span>|<span data-ttu-id="d0294-135">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="d0294-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="d0294-136">**/ILONLY+**</span><span class="sxs-lookup"><span data-stu-id="d0294-136">**/ILONLY+**</span></span>|<span data-ttu-id="d0294-137">ILONLY フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="d0294-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="d0294-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="d0294-138">**/ILONLY-**</span></span>|<span data-ttu-id="d0294-139">ILONLY フラグをクリアします。</span><span class="sxs-lookup"><span data-stu-id="d0294-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="d0294-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="d0294-140">**/nologo**</span></span>|<span data-ttu-id="d0294-141">Microsoft 著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="d0294-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="d0294-142">**/RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="d0294-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="d0294-143">CLR ヘッダー バージョンを 2.0 に戻します。</span><span class="sxs-lookup"><span data-stu-id="d0294-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="d0294-144">**/UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="d0294-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="d0294-145">CLR ヘッダー バージョンを 2.5 にアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="d0294-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="d0294-146">**注:**  アセンブリをネイティブに実行するには、CLR ヘッダー バージョン 2.5 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="d0294-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0294-147">コメント</span><span class="sxs-lookup"><span data-stu-id="d0294-147">Remarks</span></span>  
 <span data-ttu-id="d0294-148">オプションが何も指定されていない場合、CorFlags 変換ツールは指定されているアセンブリのフラグを表示します。</span><span class="sxs-lookup"><span data-stu-id="d0294-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0294-149">参照</span><span class="sxs-lookup"><span data-stu-id="d0294-149">See Also</span></span>  
 [<span data-ttu-id="d0294-150">ツール</span><span class="sxs-lookup"><span data-stu-id="d0294-150">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="d0294-151">64 ビット アプリケーション</span><span class="sxs-lookup"><span data-stu-id="d0294-151">64-bit Applications</span></span>](../../../docs/framework/64-bit-apps.md)  
 [<span data-ttu-id="d0294-152">Visual Studio 用開発者コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="d0294-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
