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
ms.openlocfilehash: 8342c79dd8b7452599af8d9782b0fbec5f83e964
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iceegen-interface"></a><span data-ttu-id="39517-102">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="39517-102">ICeeGen Interface</span></span>
<span data-ttu-id="39517-103">動的なコード コンパイルのためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="39517-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="39517-104">このインターフェイスは古い形式は使用できません。</span><span class="sxs-lookup"><span data-stu-id="39517-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39517-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-105">Methods</span></span>  
  
|<span data-ttu-id="39517-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-106">Method</span></span>|<span data-ttu-id="39517-107">説明</span><span class="sxs-lookup"><span data-stu-id="39517-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="39517-108">AddSectionReloc メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-108">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|<span data-ttu-id="39517-109">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-109">Obsolete.</span></span> <span data-ttu-id="39517-110">コード ベースを .reloc 命令を追加します。</span><span class="sxs-lookup"><span data-stu-id="39517-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="39517-111">AllocateMethodBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-111">AllocateMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="39517-112">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-112">Obsolete.</span></span> <span data-ttu-id="39517-113">メソッドで指定されたサイズのバッファーを作成し、メソッドの相対仮想アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="39517-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="39517-114">ComputePointer メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-114">ComputePointer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|<span data-ttu-id="39517-115">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-115">Obsolete.</span></span> <span data-ttu-id="39517-116">指定されたコードのセクションのバッファーを決定します。</span><span class="sxs-lookup"><span data-stu-id="39517-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="39517-117">EmitString メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-117">EmitString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|<span data-ttu-id="39517-118">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-118">Obsolete.</span></span> <span data-ttu-id="39517-119">コード ベースに、指定した文字列を出力します。</span><span class="sxs-lookup"><span data-stu-id="39517-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="39517-120">GenerateCeeFile メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-120">GenerateCeeFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|<span data-ttu-id="39517-121">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-121">Obsolete.</span></span> <span data-ttu-id="39517-122">これに現在読み込まれているコード ベースを含むコード ベースのファイルを生成`ICeeGen`です。</span><span class="sxs-lookup"><span data-stu-id="39517-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="39517-123">GenerateCeeMemoryImage メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-123">GenerateCeeMemoryImage Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|<span data-ttu-id="39517-124">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-124">Obsolete.</span></span> <span data-ttu-id="39517-125">コード ベースのメモリ内のイメージを生成します。</span><span class="sxs-lookup"><span data-stu-id="39517-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="39517-126">GetIlSection メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-126">GetIlSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|<span data-ttu-id="39517-127">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-127">Obsolete.</span></span> <span data-ttu-id="39517-128">指定されたハンドルによって参照される基本の中間言語コードのセクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="39517-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="39517-129">GetIMapTokenIface メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-129">GetIMapTokenIface Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|<span data-ttu-id="39517-130">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-130">Obsolete.</span></span> <span data-ttu-id="39517-131">指定したトークンによって参照されているインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="39517-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="39517-132">GetMethodBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-132">GetMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|<span data-ttu-id="39517-133">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-133">Obsolete.</span></span> <span data-ttu-id="39517-134">指定の相対仮想アドレスのメソッドを適切なサイズのバッファーを取得します。</span><span class="sxs-lookup"><span data-stu-id="39517-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="39517-135">GetSectionBlock メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-135">GetSectionBlock Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|<span data-ttu-id="39517-136">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-136">Obsolete.</span></span> <span data-ttu-id="39517-137">コード ベースのセクションのブロックを取得します。</span><span class="sxs-lookup"><span data-stu-id="39517-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="39517-138">GetSectionCreate メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-138">GetSectionCreate Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|<span data-ttu-id="39517-139">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-139">Obsolete.</span></span> <span data-ttu-id="39517-140">生成し、指定した名前とフラグの値を使用してコード セクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="39517-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="39517-141">GetSectionDataLen メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-141">GetSectionDataLen Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|<span data-ttu-id="39517-142">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-142">Obsolete.</span></span> <span data-ttu-id="39517-143">指定されたセクションの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="39517-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="39517-144">GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-144">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|<span data-ttu-id="39517-145">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-145">Obsolete.</span></span> <span data-ttu-id="39517-146">指定の相対仮想アドレスに格納された文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="39517-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="39517-147">GetStringSection メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-147">GetStringSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|<span data-ttu-id="39517-148">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-148">Obsolete.</span></span> <span data-ttu-id="39517-149">指定されたハンドルによって参照されるコードのセクションの文字列表現を取得します。</span><span class="sxs-lookup"><span data-stu-id="39517-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="39517-150">TruncateSection メソッド</span><span class="sxs-lookup"><span data-stu-id="39517-150">TruncateSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|<span data-ttu-id="39517-151">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="39517-151">Obsolete.</span></span> <span data-ttu-id="39517-152">指定された長さで指定したコードのセクションを切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="39517-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="39517-153">要件</span><span class="sxs-lookup"><span data-stu-id="39517-153">Requirements</span></span>  
 <span data-ttu-id="39517-154">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="39517-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39517-155">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="39517-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="39517-156">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="39517-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="39517-157">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39517-157">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39517-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="39517-158">See Also</span></span>  
 [<span data-ttu-id="39517-159">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="39517-159">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
