---
title: "ISymUnmanagedWriter::SetUserEntryPoint メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetUserEntryPoint
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be7f348237fdcf0a136d34ce3b6b8548c16d5547
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="549d9-102">ISymUnmanagedWriter::SetUserEntryPoint メソッド</span><span class="sxs-lookup"><span data-stu-id="549d9-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="549d9-103">このモジュールのエントリ ポイントは、ユーザー定義のメソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="549d9-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="549d9-104">たとえば、このエントリ ポイントは、メインの前に、コンパイラによって生成されたスタブではなく、ユーザーのメイン メソッドになります。</span><span class="sxs-lookup"><span data-stu-id="549d9-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="549d9-105">構文</span><span class="sxs-lookup"><span data-stu-id="549d9-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="549d9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="549d9-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="549d9-107">[in]ユーザーのエントリであるメソッドのメタデータ トークンをポイントします。</span><span class="sxs-lookup"><span data-stu-id="549d9-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="549d9-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="549d9-108">Return Value</span></span>  
 <span data-ttu-id="549d9-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="549d9-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="549d9-110">要件</span><span class="sxs-lookup"><span data-stu-id="549d9-110">Requirements</span></span>  
 <span data-ttu-id="549d9-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="549d9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="549d9-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="549d9-112">See Also</span></span>  
 [<span data-ttu-id="549d9-113">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="549d9-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
