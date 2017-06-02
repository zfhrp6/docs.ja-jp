---
title: "相互運用固有の属性の適用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - ".NET Framework, 公開 (COM にコンポーネントを)"
  - "属性 [.NET Framework], 変換ツール"
  - "属性 [.NET Framework], デザイン時機能"
  - "属性 [.NET Framework], 相互運用固有の"
  - "COM 相互運用機能, 適用 (属性を)"
  - "COM 相互運用機能, 公開 (COM コンポーネントを)"
  - "変換ツール属性"
  - "デザイン時属性"
  - "相互運用 (アンマネージ コードとの), 適用 (属性を)"
  - "相互運用 (アンマネージ コードとの), 公開 (.NET Framework コンポーネントを)"
ms.assetid: b6014613-641c-4912-9e2f-83a99210a037
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 相互運用固有の属性の適用
<xref:System.Runtime.InteropServices> 名前空間では、デザイン時に作成者が適用する属性、変換処理中に COM 相互運用ツールおよび API によって適用される属性、作成者または COM 相互運用機能によって適用される属性という 3 種類の相互運用固有の属性が提供されます。  
  
 マネージ コードに属性を適用する作業に習熟していない場合は、「[属性を使用したメタデータの拡張](../../../docs/standard/attributes/index.md)」を参照してください。  他のカスタム属性の場合と同様に、相互運用固有の属性は、型、メソッド、プロパティ、パラメーター、フィールド、およびその他のメンバーに対して適用できます。  
  
## デザイン時属性  
 COM 相互運用ツールおよび API によって実行された変換処理の結果を調整するには、デザイン時属性を使用します。  マネージ ソース コードに適用できる属性の説明を次の表に示します。  COM 相互運用ツールがこの表で示す属性を適用できる場合もあります。  
  
|属性|Description|  
|--------|-----------------|  
|<xref:System.Runtime.InteropServices.AutomationProxyAttribute>|Automation Marshaler またはカスタムのプロキシとスタブを使用して、型をマーシャリングするかどうかを指定します。|  
|<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>|クラスに対して生成されたインターフェイスの型を制御します。|  
|<xref:System.Runtime.InteropServices.CoClassAttribute>|タイプ ライブラリからインポートされた元のコクラスの CLSID を識別します。<br /><br /> COM 相互運用ツールでは、通常この属性が適用されます。|  
|<xref:System.Runtime.InteropServices.ComImportAttribute>|コクラスまたはインターフェイス定義が COM タイプ ライブラリからインポートされたことを示します。  ランタイムは、このフラグを使ってその型をアクティブ化およびマーシャリングする方法を識別します。  この属性は、型がタイプ ライブラリにエクスポートされることを禁止します。<br /><br /> COM 相互運用ツールでは、通常この属性が適用されます。|  
|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>|COM から使用するためにアセンブリを登録するときに、メソッドが呼び出されるようにします。これによって、登録処理中にユーザー作成コードを実行できます。|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|クラスのイベントの発生元になるインターフェイスを識別します。<br /><br /> COM 相互運用ツールでは、この属性を適用できます。|  
|<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>|アセンブリが COM から登録解除されるときメソッドが呼び出されるようにして、登録解除処理中にユーザー作成コードを実行できるようにします。|  
|<xref:System.Runtime.InteropServices.ComVisibleAttribute>|この属性の値を **false** に設定すると、型を COM から参照できなくなります。  この属性は、COM の参照可能範囲を制御するために、個別の型またはアセンブリ全体に適用できます。  既定では、すべてのパブリックなマネージ型は参照可能なので、この属性を使ってこれらの型を参照可能にする必要はありません。|  
|<xref:System.Runtime.InteropServices.DispIdAttribute>|メソッドまたはフィールドの COM ディスパッチ識別子 \(DISPID: Dispatch Identifier\) を指定します。  この属性には、対象のメソッド、フィールド、またはプロパティの DISPID が含まれています。<br /><br /> COM 相互運用ツールでは、この属性を適用できます。|  
|<xref:System.Runtime.InteropServices.FieldOffsetAttribute>|**StructLayoutAttribute** と共に使用すると、クラス内の各フィールドの物理的位置を示します。さらに、**LayoutKind** が Explicit に設定されます。|  
|<xref:System.Runtime.InteropServices.GuidAttribute>|クラス、インターフェイス、またはタイプ ライブラリ全体のグローバル一意識別子 \(GUID: Globally Unique Identifier\) を指定します。  この属性に渡す文字列は、**System.Guid** 型の受け入れ可能なコンストラクターの引数の形式であることが必要です。<br /><br /> COM 相互運用ツールでは、この属性を適用できます。|  
|[IDispatchImpAttribute](frlrfsystemruntimeinteropservicesidispatchimplattributeclasstopic)|COM にデュアル インターフェイスやディスパッチ インターフェイスを公開するときに、共通言語ランタイムで使用する **IDispatch** インターフェイスの実装の種類を示します。|  
|<xref:System.Runtime.InteropServices.InAttribute>|呼び出し元に対してデータをマーシャリングして渡すことを示します。  属性パラメーターに対して使用できます。|  
|<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>|マネージ インターフェイスを COM クライアントに公開する方法を制御します \(デュアル、IUnknown ベース、または IDispatch 限定のいずれか\)。<br /><br /> COM 相互運用ツールでは、この属性を適用できます。|  
|<xref:System.Runtime.InteropServices.LCIDConversionAttribute>|アンマネージ メソッド シグネチャが LCID パラメーターを期待していることを示します。<br /><br /> COM 相互運用ツールでは、この属性を適用できます。|  
|<xref:System.Runtime.InteropServices.MarshalAsAttribute>|マネージ コードとアンマネージ コードとの間で、フィールドまたはパラメーター内のデータをマーシャリングする方法を示します。  各データ型には既定のマーシャリング動作があるため、この属性は常に省略できます。<br /><br /> COM 相互運用ツールでは、この属性を適用できます。|  
|<xref:System.Runtime.InteropServices.OptionalAttribute>|パラメーターが省略可能であることを示します。<br /><br /> COM 相互運用ツールでは、この属性を適用できます。|  
|<xref:System.Runtime.InteropServices.OutAttribute>|フィールドまたはパラメーター内のデータが、呼び出されたオブジェクトから呼び出し元に返されるときに、マーシャリングされる必要のあることを示します。|  
|<xref:System.Runtime.InteropServices.PreserveSigAttribute>|通常は相互運用呼び出しのときに発生する、HRESULT または retval シグネチャ変換を抑止します。  この属性は、タイプ ライブラリのエクスポートだけでなく、マーシャリングにも影響します。<br /><br /> COM 相互運用ツールでは、この属性を適用できます。|  
|<xref:System.Runtime.InteropServices.ProgIdAttribute>|.NET Framework クラスの ProgID を指定します。  属性クラスに対して使用できます。|  
|<xref:System.Runtime.InteropServices.StructLayoutAttribute>|クラスのフィールドの物理レイアウトを制御します。<br /><br /> COM 相互運用ツールでは、この属性を適用できます。|  
  
## 変換ツールの属性  
 変換処理中に COM 相互運用ツールが適用する属性の説明を次の表に示します。  これらの属性は、デザイン時には適用しません。  
  
|属性|Description|  
|--------|-----------------|  
|<xref:System.Runtime.InteropServices.ComAliasNameAttribute>|パラメーターまたはフィールド型の COM エイリアスを示します。  属性パラメーター、フィールド、または戻り値に対して使用できます。|  
|<xref:System.Runtime.InteropServices.ComConversionLossAttribute>|クラスまたはインターフェイスに関する情報が、タイプ ライブラリからアセンブリにインポートされるときに失われたことを示します。|  
|<xref:System.Runtime.InteropServices.ComEventInterfaceAttribute>|ソース インターフェイスと、イベント インターフェイスのメソッドを実装するクラスを識別します。|  
|<xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>|アセンブリが元は COM タイプ ライブラリからインポートされたことを示します。  この属性は、元のタイプ ライブラリのタイプ ライブラリ定義を含んでいます。|  
|<xref:System.Runtime.InteropServices.TypeLibFuncAttribute>|元はこの関数のために COM タイプ ライブラリからインポートされた **FUNCFLAGS** を含んでいます。|  
|<xref:System.Runtime.InteropServices.TypeLibTypeAttribute>|元はこの型のために COM タイプ ライブラリからインポートされた **TYPEFLAGS** を含んでいます。|  
|<xref:System.Runtime.InteropServices.TypeLibVarAttribute>|元はこの変数のために COM タイプ ライブラリからインポートされた **VARFLAGS** を含んでいます。|  
  
## 参照  
 <xref:System.Runtime.InteropServices>   
 [COM への .NET Framework コンポーネントの公開](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [属性](../../../docs/standard/attributes/index.md)   
 [相互運用のための .NET 型の要件](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)   
 [COM 用のアセンブリのパッケージ化](../../../docs/framework/interop/packaging-an-assembly-for-com.md)