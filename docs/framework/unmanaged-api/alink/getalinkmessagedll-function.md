---
title: "GetALinkMessageDll 関数"
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
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 16657c62d66db1570ad379ff5d42a75aaf3ea2a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll 関数
検索し、メッセージ DLL を読み込みます。 メッセージ DLL があるか、読み込まれた場合は、0 を返します。 メッセージ DLL は、その名前は、言語 ID、名前のサブディレクトリに、または現在のディレクトリにする必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** alink.h  
  
 **ライブラリ**: alink.dll  
  
## <a name="see-also"></a>参照  
 [Al.exe (アセンブリ リンカー)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
