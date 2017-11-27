---
title: "CoEEShutDownCOM 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CoEEShutDownCOM
helpviewer_keywords: CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d6d9e3d650f65ef084c63104980bca0ac77f1bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM 関数
共通言語ランタイム (CLR) の内部ランタイム呼び出し可能ラッパー (RCW) を保持しているすべてのインターフェイス ポインターを解放するを強制します。 RCW のすべてのキャッシュを解放する効果があります。 このグローバル関数は非推奨、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。 代わりに、特定のランタイムのエントリ ポイントを使用します。  
  
## <a name="syntax"></a>構文  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>コメント  
 `CoEEShutDownCOM`関数は、最初のすべてのコンテキストでは、他のすべてのキャッシュにあるすべての Rcw を解放し、セットアップで既存の任意の終了処理通知を削除します。 DLL のアンロードは行われません。  
  
> [!CAUTION]
>  この関数では、プロセスに読み込まれているすべてのランタイムに影響します。  
  
 以降で、 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]、この関数に影響する特定のランタイムのエントリ ポイントを呼び出します。 エントリ ポイントを取得する、 [iclrruntimeinfo::getprocaddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)メソッド"CoEEShutDownCOM"を指定します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ グローバル静的関数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
