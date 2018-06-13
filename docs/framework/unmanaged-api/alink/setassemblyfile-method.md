---
title: SetAssemblyFile メソッド
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e557cc0da7bc684843ae3969242ffb84d811c44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405347"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="ddb19-102">SetAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="ddb19-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="ddb19-103">作成するアセンブリの名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ddb19-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="ddb19-104">非バインド モジュールを生成するときに使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ddb19-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddb19-105">構文</span><span class="sxs-lookup"><span data-stu-id="ddb19-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ddb19-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ddb19-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="ddb19-107">マニフェスト ファイルの完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="ddb19-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="ddb19-108">ポインター [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="ddb19-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="ddb19-109">定義されているフラグ[AssemblyFlags 列挙体](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="ddb19-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="ddb19-110">結果として得られるアセンブリ ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ddb19-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddb19-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="ddb19-111">Return Value</span></span>  
 <span data-ttu-id="ddb19-112">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="ddb19-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddb19-113">要件</span><span class="sxs-lookup"><span data-stu-id="ddb19-113">Requirements</span></span>  
 <span data-ttu-id="ddb19-114">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="ddb19-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddb19-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ddb19-115">See Also</span></span>  
 [<span data-ttu-id="ddb19-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ddb19-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ddb19-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ddb19-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ddb19-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="ddb19-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
