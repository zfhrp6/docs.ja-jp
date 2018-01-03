---
title: "SetManifestFile メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink3.SetManifestFile
api_location: alink.dll
api_type: COM
f1_keywords: SetManifestFile
helpviewer_keywords: SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf48153454fbb2c24dc3f1cfe1f82deefa4ee723
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="setmanifestfile-method"></a>SetManifestFile メソッド
指定するか、アセンブリの作成時に、リンカーが使用するマニフェスト ファイルをリセットできます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszFile`  
  
 内容が Win32 リソースの blob に格納するマニフェスト ファイルの名前。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は、S_OK を返します。  
  
## <a name="remarks"></a>コメント  
 これを呼び出して、Win32ResBlob を求めます。 値、`pszFile`パラメーターは、その内容の読み取りおよび RT_MANIFEST の ID では、Win32 リソースにマニフェスト ファイルの名前。 NULL のパラメーターを使用して呼び出されると、以前に読み取られたマニフェストがクリアされます。 これにより、1 つの初期化時に、リンカーの状態をリセットすることができます。  
  
## <a name="requirements"></a>必要条件  
 ALink.h が必要です。  
  
## <a name="see-also"></a>参照  
 [IALink3 インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [IALink インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Al.exe (アセンブリ リンカー)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
