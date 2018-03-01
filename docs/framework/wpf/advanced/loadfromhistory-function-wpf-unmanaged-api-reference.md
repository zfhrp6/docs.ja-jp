---
title: "LoadFromHistory 関数 (WPF アンマネージ API リファレンス)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6eca1c30664e381101b6e51c1347341432a042b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>LoadFromHistory 関数 (WPF アンマネージ API リファレンス)
この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしてをコードから直接使用するものではありません。  
  
 Windows の管理、Windows Presentation Foundation (WPF) インフラストラクチャによって使用されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a>パラメーター  
 pHistoryStream  
 履歴情報のストリームへのポインター。  
  
 pBindCtx  
 バインド コンテキストへのポインター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[.NET Framework システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **DLL:**  
  
 .NET framework 3.0 および 3.5: PresentationHostDLL.dll  
  
 .NET Framework 4 以降: PresentationHost_v0400.dll  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [WPF のアンマネージ API リファレンス](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
