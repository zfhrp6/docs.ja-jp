---
title: GetALinkMessageDll 関数
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 395dc85ad638e8a790962a4aa38019612c360ce1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402218"
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll 関数
検索し、メッセージ DLL を読み込みます。 メッセージ DLL があるか、読み込まれた場合は、0 を返します。 メッセージ DLL は、その名前は、言語 ID、名前のサブディレクトリに、または現在のディレクトリにする必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** alink.h  
  
 **ライブラリ**: alink.dll  
  
## <a name="see-also"></a>関連項目  
 [Al.exe (アセンブリ リンカー)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
