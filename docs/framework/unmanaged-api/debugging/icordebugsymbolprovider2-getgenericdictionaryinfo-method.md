---
title: "ICorDebugSymbolProvider2::GetGenericDictionaryInfo メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63126e4f34ea7ea7dee7dd0b9cae0dc0fea57ed9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="d7d51-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="d7d51-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>
<span data-ttu-id="d7d51-103">汎用のディクショナリ マップを取得します。</span><span class="sxs-lookup"><span data-stu-id="d7d51-103">Retrieves a generic dictionary map.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d51-104">構文</span><span class="sxs-lookup"><span data-stu-id="d7d51-104">Syntax</span></span>  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7d51-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d7d51-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="d7d51-106">[out]アドレスへのポインター、 [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)汎用のディクショナリ マップを含むオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d7d51-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="d7d51-107">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7d51-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7d51-108">コメント</span><span class="sxs-lookup"><span data-stu-id="d7d51-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7d51-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d7d51-109">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="d7d51-110">このマップは最上位レベルの 2 つのセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="d7d51-110">The map consists of two top-level sections:</span></span>  
  
-   <span data-ttu-id="d7d51-111">A[ディレクトリ](#Directory)のこのマップに含まれるすべてのディクショナリの相対仮想アドレス (RVA) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d7d51-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>  
  
-   <span data-ttu-id="d7d51-112">バイト揃え[ヒープ](#Heap)オブジェクトのインスタンス化情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="d7d51-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="d7d51-113">最後のディレクトリ エントリの直後から開始します。</span><span class="sxs-lookup"><span data-stu-id="d7d51-113">It starts immediately after the last directory entry.</span></span>  
  
<a name="Directory"></a>   
## <a name="the-directory"></a><span data-ttu-id="d7d51-114">ディレクトリ</span><span class="sxs-lookup"><span data-stu-id="d7d51-114">The Directory</span></span>  
 <span data-ttu-id="d7d51-115">ディレクトリ内の各エントリは、ヒープ内のオフセットを参照します。つまり、これは、ヒープの開始位置を基準としたオフセットです。</span><span class="sxs-lookup"><span data-stu-id="d7d51-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="d7d51-116">個々のエントリの値が一意とは限りません。このため、複数のディクショナリ エントリがヒープ内の同一オフセットを指すことがあります。</span><span class="sxs-lookup"><span data-stu-id="d7d51-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>  
  
 <span data-ttu-id="d7d51-117">汎用のディクショナリ マップのディレクトリ部分の構造は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d7d51-117">The directory portion of the generic dictionary map has the following structure:</span></span>  
  
-   <span data-ttu-id="d7d51-118">最初の 4 バイトには、ディクショナリのエントリ数 (ディクショナリ内の相対仮想アドレスの数) が格納されています。</span><span class="sxs-lookup"><span data-stu-id="d7d51-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="d7d51-119">この値にについて*N*です。上位ビットが設定されている場合、エントリは相対仮想アドレスに基づいて昇順で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="d7d51-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>  
  
-   <span data-ttu-id="d7d51-120">*N*ディレクトリ エントリに従います。</span><span class="sxs-lookup"><span data-stu-id="d7d51-120">The *N* directory entries follow.</span></span> <span data-ttu-id="d7d51-121">各エントリは 8 バイトであり、次の 2 つの 4 バイト セグメントからなります。</span><span class="sxs-lookup"><span data-stu-id="d7d51-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>  
  
    -   <span data-ttu-id="d7d51-122">バイト 0 ～ 3: RVA (ディクショナリの相対仮想アドレス)。</span><span class="sxs-lookup"><span data-stu-id="d7d51-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>  
  
    -   <span data-ttu-id="d7d51-123">バイト 4 ～ 7: オフセット (ヒープの開始位置を基準としたオフセット)。</span><span class="sxs-lookup"><span data-stu-id="d7d51-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>  
  
<a name="Heap"></a>   
## <a name="the-heap"></a><span data-ttu-id="d7d51-124">ヒープ</span><span class="sxs-lookup"><span data-stu-id="d7d51-124">The Heap</span></span>  
 <span data-ttu-id="d7d51-125">ヒープのサイズは、ストリーム リーダーにより、ディレクトリ サイズ + 4 の値からストリームの長さを差し引くことで算出されます。</span><span class="sxs-lookup"><span data-stu-id="d7d51-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="d7d51-126">つまり、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d7d51-126">In other words:</span></span>  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 <span data-ttu-id="d7d51-127">ディレクトリのサイズが `N * 8` であるとします。</span><span class="sxs-lookup"><span data-stu-id="d7d51-127">where the directory size is `N * 8`.</span></span>  
  
 <span data-ttu-id="d7d51-128">ヒープの各インスタンス化情報項目の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d7d51-128">The format for each instantiation information item on the heap is:</span></span>  
  
-   <span data-ttu-id="d7d51-129">このインスタンス化情報項目のバイト単位の長さ。圧縮 ECMA メタデータ形式です。</span><span class="sxs-lookup"><span data-stu-id="d7d51-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="d7d51-130">値では、この長さ情報が除外されます。</span><span class="sxs-lookup"><span data-stu-id="d7d51-130">The value excludes this length information.</span></span>  
  
-   <span data-ttu-id="d7d51-131">ジェネリックのインスタンス化の種類の数または*T*、圧縮 ECMA メタデータ形式にします。</span><span class="sxs-lookup"><span data-stu-id="d7d51-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>  
  
-   <span data-ttu-id="d7d51-132">*T* ECMA 型シグネチャ形式で表されるそれぞれの種類。</span><span class="sxs-lookup"><span data-stu-id="d7d51-132">*T* types, each represented in ECMA type signature format.</span></span>  
  
 <span data-ttu-id="d7d51-133">各ヒープ要素の長さを含めることで、ヒープに影響を与えずに、ディレクトリ セクションの単純な並べ替えを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d7d51-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7d51-134">必要条件</span><span class="sxs-lookup"><span data-stu-id="d7d51-134">Requirements</span></span>  
 <span data-ttu-id="d7d51-135">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d7d51-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7d51-136">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7d51-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7d51-137">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7d51-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7d51-138">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7d51-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7d51-139">参照</span><span class="sxs-lookup"><span data-stu-id="d7d51-139">See Also</span></span>  
 [<span data-ttu-id="d7d51-140">ICorDebugSymbolProvider2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7d51-140">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="d7d51-141">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7d51-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
