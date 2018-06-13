---
title: IAppIdAuthority インターフェイス
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 819afec2c448e5f396ab54e2dde00c01da310b12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433751"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority インターフェイス
メソッドを生成し、アプリケーションの id と参照キーの比較を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|2 つ指定されているかどうかを示す値を取得[IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)インスタンスが等しい。 フラグの値をそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡すことができます。|  
|`IAppIdAuthority::AreReferencesEqual`|2 つ指定されているかどうかを示す値を取得[IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)インスタンスが等しい。 フラグの値をそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡すことができます。|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|2 つの指定した文字列の定義が等しいかどうかを示す値を取得します。 フラグの値をそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡すことができます。|  
|`IAppIdAuthority::AreTextualReferencesEqual`|2 つの指定した文字列参照が等しいかどうかを示す値を取得します。 フラグの値をそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡すことができます。|  
|`IAppIdAuthority::CreateDefinition`|新しく生成されたインターフェイス ポインターを取得`IDefinitionAppId`を現在のスコープ内のアセンブリを表すインスタンス。|  
|`IAppIdAuthority::CreateReference`|新しく作成するインターフェイス ポインターを取得`IReferenceAppId`を表す現在のスコープ内のアセンブリ。|  
|`IAppIdAuthority::DefinitionToText`|指定した文字列形式を取得`IDefinitionAppId`、指定したフラグの値を使用します。|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|示す値を取得するかどうか、指定した`IDefinitionAppId`と`IReferenceAppId`同じアセンブリを表します。|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|指定した定義の文字列と参照文字列が同じアセンブリを表すかどうかを示す値を取得します。|  
|`IAppIdAuthority::GenerateDefinitionKey`|表す、指定した文字列のキーを取得`IDefinitionAppId`インスタンス。|  
|`IAppIdAuthority::GenerateReferenceKey`|表す、指定した文字列のキーを取得`IReferenceAppId`インスタンス。|  
|`IAppIdAuthority::HashDefinition`|指定したハッシュ キーを取得`IDefinitionAppId`インスタンス。|  
|`IAppIdAuthority::HashReference`|指定したハッシュ キーを取得`IReferenceAppId`インスタンス。|  
|`IAppIdAuthority::ReferenceToText`|指定した文字列形式を取得`IReferenceAppId`、指定したフラグの値を使用します。|  
|`IAppIdAuthority::TextToDefinition`|インターフェイス ポインターを取得、`IDefinitionAppId`を指定した文字列キーによって参照されるアセンブリを表すインスタンス。|  
|`IAppIdAuthority::TextToReference`|インターフェイス ポインターを取得、`IReferenceAppId`を指定した文字列キーによって参照されるアセンブリを表すインスタンス。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
