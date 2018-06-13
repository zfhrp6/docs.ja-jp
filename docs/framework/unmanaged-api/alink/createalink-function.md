---
title: CreateALink 関数
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e29c9c246649229900beba2fcc9ab482071ae46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400667"
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
  
## <a name="requirements"></a>要件  
 **ライブラリ**: alink.dll  
  
## <a name="see-also"></a>関連項目  
 [Al.exe (アセンブリ リンカー)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
