---
title: "AssemblyOptions 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyOptions
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ad4f9e02ed0d22009fcb8a5ac078231f2cb22e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="b78c2-102">AssemblyOptions 列挙体</span><span class="sxs-lookup"><span data-stu-id="b78c2-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="b78c2-103">アセンブリ オプションを列挙します。</span><span class="sxs-lookup"><span data-stu-id="b78c2-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b78c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="b78c2-104">Syntax</span></span>  
  
```  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a><span data-ttu-id="b78c2-105">フィールド</span><span class="sxs-lookup"><span data-stu-id="b78c2-105">Fields</span></span>  
  
|<span data-ttu-id="b78c2-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="b78c2-106">Field</span></span>|<span data-ttu-id="b78c2-107">説明</span><span class="sxs-lookup"><span data-stu-id="b78c2-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b78c2-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="b78c2-108">optAssemTitle</span></span>|<span data-ttu-id="b78c2-109">文字列 - アセンブリのタイトルを表します。</span><span class="sxs-lookup"><span data-stu-id="b78c2-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="b78c2-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="b78c2-110">optAssemDescription</span></span>|<span data-ttu-id="b78c2-111">文字列 - アセンブリの説明が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b78c2-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="b78c2-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="b78c2-112">optAssemConfig</span></span>|<span data-ttu-id="b78c2-113">文字列 - アセンブリの構成が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b78c2-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="b78c2-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="b78c2-114">optAssemOS</span></span>|<span data-ttu-id="b78c2-115">エンコードされた - 文字列:"dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion"です。</span><span class="sxs-lookup"><span data-stu-id="b78c2-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="b78c2-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="b78c2-116">optAssemProcessor</span></span>|<span data-ttu-id="b78c2-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="b78c2-117">ULONG</span></span>|  
|<span data-ttu-id="b78c2-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="b78c2-118">optAssemLocale</span></span>|<span data-ttu-id="b78c2-119">文字列 - アセンブリのロケールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b78c2-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="b78c2-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="b78c2-120">optAssemVersion</span></span>|<span data-ttu-id="b78c2-121">エンコードされた - 文字列:"Major.Minor.Build.Revision"です。</span><span class="sxs-lookup"><span data-stu-id="b78c2-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="b78c2-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="b78c2-122">optAssemCompany</span></span>|<span data-ttu-id="b78c2-123">文字列 - 会社が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b78c2-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="b78c2-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="b78c2-124">optAssemProduct</span></span>|<span data-ttu-id="b78c2-125">文字列 - 製品名を格納します。</span><span class="sxs-lookup"><span data-stu-id="b78c2-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="b78c2-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="b78c2-126">optAssemProductVersion</span></span>|<span data-ttu-id="b78c2-127">文字列 (InformationalVersion とも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="b78c2-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="b78c2-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="b78c2-128">optAssemCopyright</span></span>|<span data-ttu-id="b78c2-129">文字列 - 著作権情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b78c2-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="b78c2-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="b78c2-130">optAssemTrademark</span></span>|<span data-ttu-id="b78c2-131">文字列 - 商標情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="b78c2-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="b78c2-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="b78c2-132">optAssemKeyFile</span></span>|<span data-ttu-id="b78c2-133">String (ファイル名)。</span><span class="sxs-lookup"><span data-stu-id="b78c2-133">String (file name).</span></span>|  
|<span data-ttu-id="b78c2-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="b78c2-134">optAssemKeyName</span></span>|<span data-ttu-id="b78c2-135">文字列 (キー名)。</span><span class="sxs-lookup"><span data-stu-id="b78c2-135">String (The key name).</span></span>|  
|<span data-ttu-id="b78c2-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="b78c2-136">optAssemAlgID</span></span>|<span data-ttu-id="b78c2-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="b78c2-137">ULONG</span></span>|  
|<span data-ttu-id="b78c2-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="b78c2-138">optAssemFlags</span></span>|<span data-ttu-id="b78c2-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="b78c2-139">ULONG</span></span>|  
|<span data-ttu-id="b78c2-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="b78c2-140">optAssemHalfSign</span></span>|<span data-ttu-id="b78c2-141">Bool (DelaySign とも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="b78c2-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="b78c2-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="b78c2-142">optAssemFileVersion</span></span>|<span data-ttu-id="b78c2-143">文字列である"Major.Minor.Build.Revision"--ProductVersion と同じようにエンコードします。</span><span class="sxs-lookup"><span data-stu-id="b78c2-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="b78c2-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="b78c2-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="b78c2-145">文字列である"Major.Minor.Build.Revision"としてエンコードします。</span><span class="sxs-lookup"><span data-stu-id="b78c2-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="b78c2-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="b78c2-146">optLastAssemOption</span></span>|<span data-ttu-id="b78c2-147">要素の数のカウンターです。</span><span class="sxs-lookup"><span data-stu-id="b78c2-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b78c2-148">必要条件</span><span class="sxs-lookup"><span data-stu-id="b78c2-148">Requirements</span></span>  
 <span data-ttu-id="b78c2-149">**ヘッダー:** alink.h</span><span class="sxs-lookup"><span data-stu-id="b78c2-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="b78c2-150">**ライブラリ**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="b78c2-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b78c2-151">参照</span><span class="sxs-lookup"><span data-stu-id="b78c2-151">See Also</span></span>  
 [<span data-ttu-id="b78c2-152">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="b78c2-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
