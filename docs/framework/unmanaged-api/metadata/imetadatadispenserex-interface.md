---
title: IMetaDataDispenserEx インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d930088d6e621885d14fc4bdab2475aa27594e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx インターフェイス
拡張、 [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)メタデータ Api が現在のメタデータ スコープにどのように動作する方法を制御する機能を提供するインターフェイスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[FindAssembly メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|このメソッドは実装されていません。 呼び出された場合、E_NOTIMPL を返します。|  
|[FindAssemblyModule メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|このメソッドは実装されていません。 呼び出された場合、E_NOTIMPL を返します。|  
|[GetCORSystemDirectory メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|現在の共通言語ランタイム (CLR) を保持するディレクトリを取得します。 このメソッドは、アウト プロセスのデバッガーで使用するためだけサポートします。 別のコンポーネントから呼び出す場合、E_NOTIMPL を返します。|  
|[GetOption メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|現在のメタデータ スコープに指定されたオプションの値を取得します。 オプションは、現在のメタデータ スコープへの呼び出しの処理方法を制御します。|  
|[OpenScopeOnITypeInfo メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|このメソッドは実装されていません。 呼び出された場合、E_NOTIMPL を返します。|  
|[SetOption メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|現在のメタデータ スコープに指定された値を指定されたオプションを設定します。 オプションは、現在のメタデータ スコープへの呼び出しの処理方法を制御します。|  
  
## <a name="requirements"></a>要件  
 **Platform:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
