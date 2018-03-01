---
title: "GetWin32ResBlob メソッド"
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
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f09bfd3ccfd3ac37854d70c226f40b17f86ccf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getwin32resblob-method"></a>GetWin32ResBlob メソッド
Win32 リソースの blob を取得します。 アセンブリ オプションを設定した後、このメソッドを呼び出します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a>パラメーター  
 `AssemblyID`  
 アセンブリの ID です。  
  
 `FileToken`  
 Win32 バージョン リソースを構築するときに使用されるファイル名の取得に使用されるファイルのトークン  
  
 `fDll`  
 ファイルが DLL の場合、false は EXE の場合は TRUE です。  
  
 `pszIconFile`  
 リソースの blob に挿入する省略可能なアイコンです。  
  
 `ppResBlob`  
 リソースの blob を受信します。  
  
 `pcbResBlob`  
 Blob のサイズを受け取ります。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は、S_OK を返します。  
  
## <a name="requirements"></a>必要条件  
 Alink.h が必要です。  
  
## <a name="see-also"></a>参照  
 [IALink インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
