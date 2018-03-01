---
title: "CreateALink 関数"
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
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 54a5afd8ee42fa122f3e18415be0b1d06c2f9302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createalink-function"></a>CreateALink 関数
アセンブリ リンカーのインスタンスを作成し、指定されたインターフェイスへのポインターを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`riid`|アセンブリ リンカー インターフェイスの 1 つの物理名。|  
|`ppInterface`|正常に終了へのポインターを格納する場所、`riid`インターフェイスです。|  
  
## <a name="requirements"></a>必要条件  
 **ライブラリ**: alink.dll  
  
## <a name="see-also"></a>参照  
 [Al.exe (アセンブリ リンカー)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
