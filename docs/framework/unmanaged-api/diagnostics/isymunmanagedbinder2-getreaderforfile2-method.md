---
title: "ISymUnmanagedBinder2::GetReaderForFile2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 270a154c40b85ad4774bececf12685393f4d6c58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="b60f1-102">ISymUnmanagedBinder2::GetReaderForFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="b60f1-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="b60f1-103">メタデータ インターフェイスおよびファイル名を指定して、正しい返します <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> をモジュールに関連付けられているデバッグ シンボルを読み取る。</span><span class="sxs-lookup"><span data-stu-id="b60f1-103">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="b60f1-104">このメソッドより広範囲の検索よりもプログラム データベース (PDB) ファイル、 [isymunmanagedbinder::getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b60f1-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b60f1-105">構文</span><span class="sxs-lookup"><span data-stu-id="b60f1-105">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b60f1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b60f1-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="b60f1-107">[in]メタデータ インポート インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b60f1-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="b60f1-108">[in]ファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b60f1-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="b60f1-109">[in]検索パスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b60f1-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="b60f1-110">[in]値、 [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)シンボル リーダーの検索を実行するときに使用されるポリシーを指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="b60f1-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b60f1-111">[out]設定されているポインターに返された <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="b60f1-111">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b60f1-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="b60f1-112">Return Value</span></span>  
 <span data-ttu-id="b60f1-113">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="b60f1-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b60f1-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="b60f1-114">Requirements</span></span>  
 <span data-ttu-id="b60f1-115">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b60f1-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b60f1-116">コメント</span><span class="sxs-lookup"><span data-stu-id="b60f1-116">Remarks</span></span>  
 <span data-ttu-id="b60f1-117">このバージョンのメソッドは、モジュールの横に以外の領域の PDB ファイルを検索できます。</span><span class="sxs-lookup"><span data-stu-id="b60f1-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="b60f1-118">検索ポリシーを結合することで制御できる[CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="b60f1-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="b60f1-119">たとえば、`AllowReferencePathAccess | AllowSymbolServerAccess`実行可能ファイルの横にあると、シンボル サーバーの PDB の検索が、レジストリの照会またはしません、実行可能ファイルのパスを使用します。</span><span class="sxs-lookup"><span data-stu-id="b60f1-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="b60f1-120">場合、`searchPath`パラメーターを指定し、常にこれらのディレクトリが検索されます。</span><span class="sxs-lookup"><span data-stu-id="b60f1-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b60f1-121">参照</span><span class="sxs-lookup"><span data-stu-id="b60f1-121">See Also</span></span>  
 [<span data-ttu-id="b60f1-122">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b60f1-122">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="b60f1-123">GetReaderForFile メソッド</span><span class="sxs-lookup"><span data-stu-id="b60f1-123">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
