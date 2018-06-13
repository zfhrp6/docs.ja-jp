---
title: Fusion グローバル静的関数
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86cb59c0935c193a9865d5ace5fe11c96226d9e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435905"
---
# <a name="fusion-global-static-functions"></a>Fusion グローバル静的関数
このセクションでは、fusion API が使用されるアンマネージ グローバル静的関数について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ClearDownloadCache 関数](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 ダウンロードされたアセンブリのグローバル アセンブリ キャッシュをクリアします。  
  
 [CompareAssemblyIdentity 関数](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 それらが等しいかどうかを決定する 2 つのアセンブリ id を比較します。  
  
 [CreateApplicationContext 関数](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 内部使用のみ。 (この関数は、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません)。  
  
 [CreateAssemblyCache 関数](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 新しいへのポインターを取得[IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)をグローバル アセンブリ キャッシュを表すインスタンス。  
  
 [CreateAssemblyEnum 関数](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 ポインターを取得、 [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)を指定したアセンブリ内に存在するオブジェクトの一覧を表すインスタンス。  
  
 [CreateAssemblyNameObject 関数](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 ポインターを取得、 [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)を指定した名前を持つアセンブリの一意の id を表すインスタンス。  
  
 [CreateHistoryReader 関数](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 指定したファイルの履歴のリーダーを作成します。  
  
 [CreateInstallReferenceEnum 関数](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 ポインターを取得、 [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)を指定したアセンブリへのアプリケーションの参照の一覧を表すインスタンス。  
  
 [GetAppIdAuthority 関数](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 ポインターを取得、 [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)アプリケーション id と参照のキーを管理するインスタンス。  
  
 [GetAssemblyIdentityFromFile 関数](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 ポインターを取得、`IUnknown`指定したオブジェクト`IID`のアセンブリにある指定したファイル パス。  
  
 [GetCachePath 関数](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 指定したフラグを使用して、キャッシュされたアセンブリへのパスを取得します。  
  
 [GetHistoryFileDirectory 関数](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 アプリケーション履歴ディレクトリのパスを取得します。  
  
 [GetIdentityAuthority 関数](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 ポインターを取得、 [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)コード オブジェクトのキーを管理するインスタンス。  
  
 [IsFrameworkAssembly 関数](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 指定したアセンブリが管理されているかどうかを示す値を取得します。  
  
 [NukeDownloadedCache 関数](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 共通言語ランタイムのダウンロード キャッシュを削除します。  
  
 [PreBindAssemblyEx 関数](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 アセンブリのポリシー適用後の表示名を取得します。  
  
## <a name="related-sections"></a>関連項目  
 [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [Fusion 列挙型](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [Fusion 構造体](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [グローバル アセンブリ キャッシュ](../../../../docs/framework/app-domains/gac.md)
