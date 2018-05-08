---
title: ICorDebugProcess6::EnableVirtualModuleSplitting メソッド
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4565deddee2e7714d937bf61574243cc07a4602
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>ICorDebugProcess6::EnableVirtualModuleSplitting メソッド
仮想モジュール分割を有効または無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `enableSplitting`  
 仮想モジュール分割を有効にするには、`true`。無効にするには、`false`。  
  
## <a name="remarks"></a>コメント  
 仮想モジュール分割原因[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)をビルド中にマージされたモジュールが処理され、1 つの大規模なモジュールではなく、個別のモジュールのグループとして表さを認識します。 これにさまざまな動作を変更[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)メソッドを次に説明します。  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
 このメソッドを呼び出し、`enableSplitting` の値をいつでも変更できます。 ステートフル関数変更は行われません、 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)で示されているメソッドの動作を変更する以外のオブジェクト、[仮想モジュール分割とアンマネージ デバッグ Api](#APIs)呼び出された時点で参照してください。 仮想モジュールを使用しても、これらのメソッドの呼び出し時にパフォーマンスの低下は発生しません。 さらに、仮想化されたメタデータの重大なメモリ内キャッシュ必要がありますを正しく実装する、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)仮想モジュール分割がオフになった後も、Api、およびこれらのキャッシュを保持可能性があります。  
  
## <a name="terminology"></a>用語  
 仮想モジュール分割について説明する場合には、次の用語が使用されます。  
  
 コンテナー モジュールまたはコンテナー  
 集計モジュール。  
  
 サブモジュール、または仮想モジュール  
 コンテナー内にあるモジュール。  
  
 標準モジュール  
 ビルド時にマージされなかったモジュール。 コンテナー モジュールでもサブモジュールでもありません。  
  
 ICorDebugModule インターフェイス オブジェクトでは、コンテナー モジュールとサブモジュールの両方が表されます。 ただし、インターフェイスの動作は、各ケースで若干異なるとして、\<セクションに x-ref > セクションについて説明します。  
  
## <a name="modules-and-assemblies"></a>モジュールとアセンブリ  
 アセンブリ マージ シナリオではマルチモジュール アセンブリはサポートされないため、モジュールとアセンブリの間には一対一リレーションシップがあります。 コンテナー モジュールまたはサブモジュールを表すかどうかに関係なく、各 ICorDebugModule オブジェクトには、対応する ICorDebugAssembly オブジェクトがあります。 [Icordebugmodule::getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)メソッドは、モジュールからアセンブリに変換します。 その他の方向にマップするため、 [icordebugassembly::enumeratemodules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)メソッドを 1 つだけのモジュールを列挙します。 この場合、アセンブリとモジュールは緊密に結合されたペアとなるため、アセンブリとモジュールはほぼ同義の用語となります。  
  
## <a name="behavioral-differences"></a>動作の違い  
 コンテナー モジュールには、次の動作と特性があります。  
  
-   構成要素であるすべてのサブモジュールのメタデータはマージされます。  
  
-   型名は変形する可能性があります。  
  
-   [Icordebugmodule::getname](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)メソッドは、ディスク上のモジュールへのパスを返します。  
  
-   [Icordebugmodule::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)メソッドは、そのイメージのサイズを返します。  
  
-   ICorDebugAssembly3.EnumerateContainedAssemblies メソッドは、サブモジュールを一覧表示します。  
  
-   ICorDebugAssembly3.GetContainerAssembly メソッドは、`S_FALSE` を返します。  
  
 サブモジュールには、次の動作と特性があります。  
  
-   マージされた元のアセンブリのみに対応する削減されたメタデータのセットがあります。  
  
-   メタデータ名は、変形しません。  
  
-   メタデータ トークンは、ビルド プロセスでマージされる前の元のアセンブリ内のトークンと一致することはほとんどありません。  
  
-   [Icordebugmodule::getname](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)メソッド アセンブリ名、ファイル パスではなくを返します。  
  
-   [Icordebugmodule::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)メソッドは、元のマージされていないイメージのサイズを返します。  
  
-   ICorDebugModule3.EnumerateContainedAssemblies メソッドは、`S_FALSE` を返します。  
  
-   ICorDebugAssembly3.GetContainerAssembly メソッドは、格納しているモジュールを返します。  
  
## <a name="interfaces-retrieved-from-modules"></a>モジュールから取得されるインターフェイス  
 さまざまなインターフェイスをモジュールから作成または取得できます。 その例には次のものがあります。  
  
-   ICorDebugClass オブジェクトによって返される、 [icordebugmodule::getclassfromtoken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)メソッドです。  
  
-   ICorDebugAssembly オブジェクトによって返される、 [icordebugmodule::getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)メソッドです。  
  
 これらのオブジェクトは常にキャッシュ[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)が作成またはコンテナー モジュールまたはサブモジュールから照会されたのかどうかに関係なく、同じポインター id が必要であるとします。 サブモジュールは、独自のコピーを持つ個別のキャッシュではなく、これらのキャッシュされたオブジェクトのフィルター処理されたビューを提供します。  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>仮想モジュール分割とアンマネージ デバッグ API  
 次の表に、仮想モジュール分割がアンマネージ デバッグ API の他のメソッドの動作に影響する方法を示します。  
  
|メソッド|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[Icordebugfunction::getmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|この関数が最初に定義されたサブモジュールを返します|この関数がマージされたコンテナー モジュールを返します|  
|[Icordebugclass::getmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|このクラスが最初に定義されたサブモジュールを返します。|このクラスがマージされたコンテナー モジュールを返します。|  
|ICorDebugModuleDebugEvent::GetModule|読み込まれたコンテナー モジュールを返します。 サブモジュールは、この設定に関係なく、読み込みイベントを提供されません。|読み込まれたコンテナー モジュールを返します。|  
|[Icordebugappdomain::enumerateassemblies](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|サブアセンブリと標準アセンブリのリストを返します。コンテナー アセンブリは含まれません。 **注:** 任意のコンテナー アセンブリのシンボルがない場合そのサブアセンブリのいずれも列挙されます。 いずれかの標準アセンブリにシンボルがない場合、列挙される場合と列挙されない場合があります。|コンテナー アセンブリと標準アセンブリのリストを返します。サブアセンブリは含まれません。 **注:** 可能性がありますが、標準のアセンブリのシンボルがない場合、または列挙されない場合があります。|  
|[Icordebugcode::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (を参照する際の IL コードのみ)|マージ前のアセンブリ イメージ内で有効な IL を返します。 具体的には、参照先の型が IL を含む仮想モジュールで定義されていない場合、インライン メタデータ トークンは正確に TypeRef または MemberRef トークンになります。 これらの TypeRef または MemberRef トークン検索できます、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)の対応する仮想 ICorDebugModule オブジェクトのオブジェクト。|マージ後のアセンブリ イメージ内の IL を返します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugProcess6 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
