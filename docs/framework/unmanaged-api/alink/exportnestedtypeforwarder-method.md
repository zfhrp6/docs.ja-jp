---
title: "ExportNestedTypeForwarder メソッド"
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
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eee41e9f71d600a74cc9f74b538ad9e215f0d905
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="exportnestedtypeforwarder-method"></a>ExportNestedTypeForwarder メソッド
指定したアセンブリの型のテーブルを入れ子にされた型の型フォワーダーを追加します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a>パラメーター  
 `AssemblyID`  
 エクスポートするアセンブリの ID。  
  
 `FileToken`  
 ファイルの種類を定義するファイルのトークンまたはアセンブリの ID。  
  
 `TypeToken`  
 型のトークンです。  
  
 `ParentType`  
 親の種類のトークンです。  
  
 `pszTypename`  
 エクスポートする完全修飾型名。  
  
 `dwFlags`  
 `ComType`フラグのように`tdPublic`または`tdNested`です。  
  
 `pType`  
 エクスポート型のトークンを受け取ります。 これは、入れ子にされた型の生成にのみ必要です。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は、S_OK を返します。  
  
## <a name="requirements"></a>必要条件  
 Alink.h が必要です。  
  
## <a name="see-also"></a>参照  
 [IALink インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
