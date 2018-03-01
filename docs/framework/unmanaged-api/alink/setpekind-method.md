---
title: "SetPEKind メソッド"
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
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3ad300d86dadd470d0a2d50d5d6deac5bd0bad71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="setpekind-method"></a>SetPEKind メソッド
ポータブル実行可能ファイルの種類、コンピューター固有またはコンピューターにもとらわれないのいずれかを判断します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a>パラメーター  
 `AssemblyID`  
 アセンブリの ID です。  
  
 `FileToken`  
 PE の種類を設定する対象のファイルのトークン。 場合、NULL を指定できます`AssemblyID`はバインドされていない netmodule を示しません。  
  
 `dwPEKind`  
 によって示される、PE の種類、 [CorPEKind 列挙型](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)です。  
  
 `dwMachine`  
 ターゲット コンピューターのアーキテクチャ、NT ヘッダーで指定されています。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は、S_OK を返します。  
  
## <a name="requirements"></a>必要条件  
 Alink.h が必要です。  
  
## <a name="see-also"></a>参照  
 [GetPEKind メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)  
 [IALink2 インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
