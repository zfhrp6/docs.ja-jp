---
title: ISymUnmanagedWriter::SetUserEntryPoint メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9ec44d4c2757555c74fe7fc27c26cc5fc87c4517
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426688"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="3e305-102">ISymUnmanagedWriter::SetUserEntryPoint メソッド</span><span class="sxs-lookup"><span data-stu-id="3e305-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="3e305-103">このモジュールのエントリ ポイントは、ユーザー定義のメソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="3e305-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="3e305-104">たとえば、このエントリ ポイントは、メインの前に、コンパイラによって生成されたスタブではなく、ユーザーのメイン メソッドになります。</span><span class="sxs-lookup"><span data-stu-id="3e305-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e305-105">構文</span><span class="sxs-lookup"><span data-stu-id="3e305-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e305-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3e305-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="3e305-107">[in]ユーザーのエントリであるメソッドのメタデータ トークンをポイントします。</span><span class="sxs-lookup"><span data-stu-id="3e305-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e305-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="3e305-108">Return Value</span></span>  
 <span data-ttu-id="3e305-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="3e305-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e305-110">要件</span><span class="sxs-lookup"><span data-stu-id="3e305-110">Requirements</span></span>  
 <span data-ttu-id="3e305-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3e305-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e305-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e305-112">See Also</span></span>  
 [<span data-ttu-id="3e305-113">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e305-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
