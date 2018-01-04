---
title: "ICeeGen インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen
helpviewer_keywords: ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73af58ac55fd22e5b4f19f715cb0b1a137a640a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iceegen-interface"></a><span data-ttu-id="79462-102">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79462-102">ICeeGen Interface</span></span>
<span data-ttu-id="79462-103">動的なコード コンパイルのためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="79462-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="79462-104">このインターフェイスは古い形式は使用できません。</span><span class="sxs-lookup"><span data-stu-id="79462-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79462-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-105">Methods</span></span>  
  
|<span data-ttu-id="79462-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-106">Method</span></span>|<span data-ttu-id="79462-107">説明</span><span class="sxs-lookup"><span data-stu-id="79462-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79462-108">AddSectionReloc メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-108">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|<span data-ttu-id="79462-109">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-109">Obsolete.</span></span> <span data-ttu-id="79462-110">コード ベースを .reloc 命令を追加します。</span><span class="sxs-lookup"><span data-stu-id="79462-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="79462-111">AllocateMethodBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-111">AllocateMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="79462-112">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-112">Obsolete.</span></span> <span data-ttu-id="79462-113">メソッドで指定されたサイズのバッファーを作成し、メソッドの相対仮想アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="79462-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="79462-114">ComputePointer メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-114">ComputePointer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|<span data-ttu-id="79462-115">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-115">Obsolete.</span></span> <span data-ttu-id="79462-116">指定されたコードのセクションのバッファーを決定します。</span><span class="sxs-lookup"><span data-stu-id="79462-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="79462-117">EmitString メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-117">EmitString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|<span data-ttu-id="79462-118">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-118">Obsolete.</span></span> <span data-ttu-id="79462-119">コード ベースに、指定した文字列を出力します。</span><span class="sxs-lookup"><span data-stu-id="79462-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="79462-120">GenerateCeeFile メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-120">GenerateCeeFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|<span data-ttu-id="79462-121">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-121">Obsolete.</span></span> <span data-ttu-id="79462-122">これに現在読み込まれているコード ベースを含むコード ベースのファイルを生成`ICeeGen`です。</span><span class="sxs-lookup"><span data-stu-id="79462-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="79462-123">GenerateCeeMemoryImage メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-123">GenerateCeeMemoryImage Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|<span data-ttu-id="79462-124">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-124">Obsolete.</span></span> <span data-ttu-id="79462-125">コード ベースのメモリ内のイメージを生成します。</span><span class="sxs-lookup"><span data-stu-id="79462-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="79462-126">GetIlSection メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-126">GetIlSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|<span data-ttu-id="79462-127">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-127">Obsolete.</span></span> <span data-ttu-id="79462-128">指定されたハンドルによって参照される基本の中間言語コードのセクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="79462-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="79462-129">GetIMapTokenIface メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-129">GetIMapTokenIface Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|<span data-ttu-id="79462-130">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-130">Obsolete.</span></span> <span data-ttu-id="79462-131">指定したトークンによって参照されているインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="79462-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="79462-132">GetMethodBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-132">GetMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|<span data-ttu-id="79462-133">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-133">Obsolete.</span></span> <span data-ttu-id="79462-134">指定の相対仮想アドレスのメソッドを適切なサイズのバッファーを取得します。</span><span class="sxs-lookup"><span data-stu-id="79462-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="79462-135">GetSectionBlock メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-135">GetSectionBlock Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|<span data-ttu-id="79462-136">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-136">Obsolete.</span></span> <span data-ttu-id="79462-137">コード ベースのセクションのブロックを取得します。</span><span class="sxs-lookup"><span data-stu-id="79462-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="79462-138">GetSectionCreate メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-138">GetSectionCreate Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|<span data-ttu-id="79462-139">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-139">Obsolete.</span></span> <span data-ttu-id="79462-140">生成し、指定した名前とフラグの値を使用してコード セクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="79462-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="79462-141">GetSectionDataLen メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-141">GetSectionDataLen Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|<span data-ttu-id="79462-142">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-142">Obsolete.</span></span> <span data-ttu-id="79462-143">指定されたセクションの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="79462-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="79462-144">GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-144">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|<span data-ttu-id="79462-145">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-145">Obsolete.</span></span> <span data-ttu-id="79462-146">指定の相対仮想アドレスに格納された文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="79462-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="79462-147">GetStringSection メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-147">GetStringSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|<span data-ttu-id="79462-148">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-148">Obsolete.</span></span> <span data-ttu-id="79462-149">指定されたハンドルによって参照されるコードのセクションの文字列表現を取得します。</span><span class="sxs-lookup"><span data-stu-id="79462-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="79462-150">TruncateSection メソッド</span><span class="sxs-lookup"><span data-stu-id="79462-150">TruncateSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|<span data-ttu-id="79462-151">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="79462-151">Obsolete.</span></span> <span data-ttu-id="79462-152">指定された長さで指定したコードのセクションを切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="79462-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79462-153">必要条件</span><span class="sxs-lookup"><span data-stu-id="79462-153">Requirements</span></span>  
 <span data-ttu-id="79462-154">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="79462-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79462-155">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="79462-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79462-156">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="79462-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="79462-157">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79462-157">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79462-158">参照</span><span class="sxs-lookup"><span data-stu-id="79462-158">See Also</span></span>  
 [<span data-ttu-id="79462-159">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79462-159">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
