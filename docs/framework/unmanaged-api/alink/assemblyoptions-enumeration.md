---
title: AssemblyOptions 列挙体
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3926a0d49b2db02cf52a3cc943b05edc4cc36a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406286"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="d2445-102">AssemblyOptions 列挙体</span><span class="sxs-lookup"><span data-stu-id="d2445-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="d2445-103">アセンブリ オプションを列挙します。</span><span class="sxs-lookup"><span data-stu-id="d2445-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2445-104">構文</span><span class="sxs-lookup"><span data-stu-id="d2445-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="d2445-105">フィールド</span><span class="sxs-lookup"><span data-stu-id="d2445-105">Fields</span></span>  
  
|<span data-ttu-id="d2445-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="d2445-106">Field</span></span>|<span data-ttu-id="d2445-107">説明</span><span class="sxs-lookup"><span data-stu-id="d2445-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d2445-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="d2445-108">optAssemTitle</span></span>|<span data-ttu-id="d2445-109">文字列 - アセンブリのタイトルを表します。</span><span class="sxs-lookup"><span data-stu-id="d2445-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="d2445-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="d2445-110">optAssemDescription</span></span>|<span data-ttu-id="d2445-111">文字列 - アセンブリの説明が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d2445-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="d2445-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="d2445-112">optAssemConfig</span></span>|<span data-ttu-id="d2445-113">文字列 - アセンブリの構成が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d2445-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="d2445-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="d2445-114">optAssemOS</span></span>|<span data-ttu-id="d2445-115">エンコードされた - 文字列:"dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion"です。</span><span class="sxs-lookup"><span data-stu-id="d2445-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="d2445-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="d2445-116">optAssemProcessor</span></span>|<span data-ttu-id="d2445-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="d2445-117">ULONG</span></span>|  
|<span data-ttu-id="d2445-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="d2445-118">optAssemLocale</span></span>|<span data-ttu-id="d2445-119">文字列 - アセンブリのロケールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d2445-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="d2445-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="d2445-120">optAssemVersion</span></span>|<span data-ttu-id="d2445-121">エンコードされた - 文字列:"Major.Minor.Build.Revision"です。</span><span class="sxs-lookup"><span data-stu-id="d2445-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="d2445-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="d2445-122">optAssemCompany</span></span>|<span data-ttu-id="d2445-123">文字列 - 会社が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d2445-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="d2445-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="d2445-124">optAssemProduct</span></span>|<span data-ttu-id="d2445-125">文字列 - 製品名を格納します。</span><span class="sxs-lookup"><span data-stu-id="d2445-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="d2445-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="d2445-126">optAssemProductVersion</span></span>|<span data-ttu-id="d2445-127">文字列 (InformationalVersion とも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="d2445-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="d2445-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="d2445-128">optAssemCopyright</span></span>|<span data-ttu-id="d2445-129">文字列 - 著作権情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d2445-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="d2445-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="d2445-130">optAssemTrademark</span></span>|<span data-ttu-id="d2445-131">文字列 - 商標情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="d2445-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="d2445-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="d2445-132">optAssemKeyFile</span></span>|<span data-ttu-id="d2445-133">String (ファイル名)。</span><span class="sxs-lookup"><span data-stu-id="d2445-133">String (file name).</span></span>|  
|<span data-ttu-id="d2445-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="d2445-134">optAssemKeyName</span></span>|<span data-ttu-id="d2445-135">文字列 (キー名)。</span><span class="sxs-lookup"><span data-stu-id="d2445-135">String (The key name).</span></span>|  
|<span data-ttu-id="d2445-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="d2445-136">optAssemAlgID</span></span>|<span data-ttu-id="d2445-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="d2445-137">ULONG</span></span>|  
|<span data-ttu-id="d2445-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="d2445-138">optAssemFlags</span></span>|<span data-ttu-id="d2445-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="d2445-139">ULONG</span></span>|  
|<span data-ttu-id="d2445-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="d2445-140">optAssemHalfSign</span></span>|<span data-ttu-id="d2445-141">Bool (DelaySign とも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="d2445-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="d2445-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="d2445-142">optAssemFileVersion</span></span>|<span data-ttu-id="d2445-143">文字列である"Major.Minor.Build.Revision"--ProductVersion と同じようにエンコードします。</span><span class="sxs-lookup"><span data-stu-id="d2445-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="d2445-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="d2445-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="d2445-145">文字列である"Major.Minor.Build.Revision"としてエンコードします。</span><span class="sxs-lookup"><span data-stu-id="d2445-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="d2445-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="d2445-146">optLastAssemOption</span></span>|<span data-ttu-id="d2445-147">要素の数のカウンターです。</span><span class="sxs-lookup"><span data-stu-id="d2445-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2445-148">要件</span><span class="sxs-lookup"><span data-stu-id="d2445-148">Requirements</span></span>  
 <span data-ttu-id="d2445-149">**ヘッダー:** alink.h</span><span class="sxs-lookup"><span data-stu-id="d2445-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="d2445-150">**ライブラリ**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="d2445-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2445-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2445-151">See Also</span></span>  
 [<span data-ttu-id="d2445-152">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="d2445-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
