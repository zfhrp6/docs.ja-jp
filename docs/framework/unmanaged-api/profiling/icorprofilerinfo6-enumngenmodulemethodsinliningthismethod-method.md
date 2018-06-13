---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod メソッド
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 564f3b1cdfab2a3020b6bb5ac8d9af03c6532c8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459672"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod メソッド
[.NET Framework 4.6 およびそれ以降のバージョンでサポート]  
  
 特定の NGen モジュールとインライン特定のメソッドで定義されているすべてのメソッドを列挙子を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `inlinersModuleId`  
 [in]NGen モジュールの識別子。  
  
 `inlineeModuleId`  
 [in]定義するモジュールの識別子`inlineeMethodId`です。 詳細については、次の「解説」を参照してください。  
  
 `inlineeMethodId`  
 [in]インライン関数では、メソッドの識別子。 詳細については、次の「解説」を参照してください。  
  
 `incompleteData`  
 [out]フラグを示すかどうか`ppEnum`特定のメソッドにはインライン展開のすべてのメソッドが含まれています。  詳細については、次の「解説」を参照してください。  
  
 `ppEnum`  
 [out]列挙子のアドレスへのポインター  
  
## <a name="remarks"></a>コメント  
 `inlineeModuleId` および`inlineeMethodId`インライン展開できない可能性があります、メソッドの完全な識別子を形成します。 たとえば、モジュール`A`メソッドを定義`Simple.Add`:  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 モジュール Bdefines `Fancy.AddTwice`:  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 によりもあると想定`Fancy.AddTwice`インライン呼び出しを`SimpleAdd`です。 プロファイラーは、この列挙子を使用してモジュール B でどのインラインで定義されたすべてのメソッドを検索する可能性があります`Simple.Add`、結果の列挙は、`AddTwice`です。  `inlineeModuleId` モジュールの識別子は、 `A`、および`inlineeeMethodId`の識別子は、`Simple.Add(int a, int b)`です。  
  
 場合`incompleteData`が関数の後に true を返します、列挙子は、インライン展開のすべてのメソッドの指定されたメソッドを含んでいませんしません。 これは、1 つの場合に発生することができますかより直接的または間接的な依存関係のインライン モジュールをまだ読み込まれていません。 プロファイラーは、データの正確性を必要とする場合、複数のモジュールが読み込まれるときに、可能であれば 各モジュールの読み込み後に再試行する必要があります。  
  
 `EnumNgenModuleMethodsInliningThisMethod`で制限を回避するメソッドを使用できます ReJIT のインライン展開されます。 ReJIT により、プロファイラー メソッドの実装を変更し、その場での新しいコードを作成できます。 たとえば、変更お`Simple.Add`次のようにします。  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 ただしため`Fancy.AddTwice`がインライン関数では既に`Simple.Add`、これは引き続き以前と同様の動作は同じにします。 その制限を回避するには、呼び出し元がすべてのモジュールにそのインラインのすべてのメソッドを検索する`Simple.Add`を使用して`ICorProfilerInfo5::RequestRejit`これらのメソッドごとにします。 新しい動作は、メソッドは、再コンパイル、`Simple.Add`従来の動作の代わりにします。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerInfo6 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
