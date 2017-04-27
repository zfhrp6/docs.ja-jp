---
title: ".NET Framework 4.5.1 における再ターゲットの変更点 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- retargeting changes
- .NET Framework 4.5.1
- retargeting changes, .NET Framework 4.5.1
- retargeting changes, .NET Framework
ms.assetid: 8087326d-77e9-4804-ba33-ff1bb1bec2b8
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0c497561254c0f97f22ac05c7d44224b30ef74d0
ms.lasthandoff: 04/18/2017

---
# <a name="retargeting-changes-in-the-net-framework-451"></a>.NET Framework 4.5.1 における再ターゲットの変更点
まれに、変更を再ターゲットすると [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] を対象として再コンパイルされるアプリに影響する場合があります。 これらは、以前のバージョンの .NET Framework を対象とするバイナリには影響を与えませんが、Version 4.5.1 で実行されるバイナリには影響します。 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] には、次の領域の変更の再ターゲットが含まれます。  
  
-   [コア](#Core)  
  
-   [ADO.NET](#ADO)  
  
-   [MSBuild](#MSBuild)  
  
 次の表の [スコープ] 列には、各変更の重要度を指定します。  
  
-   メジャー。 多数のアプリに影響するか、またはコードに大幅な変更が必要な、重大な変更。 変更の再ターゲットはこのカテゴリに分類されないことに注意してください。  
  
-   マイナー。 少数のアプリに影響するか、またはコードにわずかな変更が必要な、変更。  
  
-   エッジ。 一般的ではない特定のシナリオでアプリに影響を与える変更。  
  
-   透過。 アプリの開発者やユーザーには大きな影響を及ぼさない変更。 アプリはこの変更のために変更を加える必要はありません。  
  
<a name="Core"></a>   
## <a name="core-retargeting-changes"></a>コアでの変更の再ターゲット  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.ObsoleteAttribute?displayProperty=fullName> 属性|Windows メタデータ ライブラリ (.winmd ファイル) を作成するとき、<xref:System.ObsoleteAttribute> 属性は <xref:System.ObsoleteAttribute> と [Windows.Foundation.DeprecatedAttribute](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.deprecatedattribute.aspx) の両方としてエクスポートされます。|<xref:System.ObsoleteAttribute> 属性を使用する既存のソース コードを再コンパイルして、C++/CX または JavaScript からそのコードを実行すると、警告が生成されることがあります。<br /><br /> <xref:System.ObsoleteAttribute> と [Windows.Foundation.DeprecatedAttribute](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.deprecatedattribute.aspx) の両方をマネージ アセンブリのコードに適用することはお勧めしません。ビルド警告が表示されることがあります。<br /><br /> 詳細については、<xref:System.ObsoleteAttribute> リファレンス トピックを参照してください。|エッジ|  
  
<a name="ADO"></a>   
## <a name="adonet-retargeting-changes"></a>ADO.NET での変更の再ターゲット  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Data.Common.DbParameter?displayProperty=fullName> クラス|<xref:System.Data.Common.DbParameter.Precision%2A?displayProperty=fullName> および <xref:System.Data.Common.DbParameter.Scale%2A?displayProperty=fullName> は、パブリック仮想プロパティとして実装されます。 これらは、対応する明示的なインターフェイスの実装 (<xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision%2A?displayProperty=fullName> および <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale%2A?displayProperty=fullName>) を置き換えます。|変更は、ADO.NET データベース プロバイダーをビルドする開発者にのみ影響します。|エッジ|  
  
<a name="MSBuild"></a>   
## <a name="msbuild-retargeting-changes"></a>MSBuild での変更の再ターゲット  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|`ResolveAssemblyReference` タスク|タスクは警告 MSB3270 を生成します。これは参照または依存関係がアプリのアーキテクチャと一致しないことを示します。 たとえば、`anycpu` オプションでコンパイルされたアプリに x86 参照が含まれる場合に発生します。 このようなシナリオは、実行時にアプリでエラーが起こった場合に発生することがあります (この場合は、アプリが x64 プロセスとして配置されている場合)。|影響には 2 つの領域があります。<br /><br /> -   再コンパイルすると、アプリが MSBuild の以前のバージョンでコンパイルされたときには現れなかった警告が生成されます。 ただし、警告はランタイム エラーの可能性のある原因を特定するため、調査と対処が必要です。<br />-   警告がエラーとして扱われると、アプリはコンパイルされません。|Minor|  
  
## <a name="see-also"></a>関連項目  
 [ランタイムの変更点](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)   
 [4.5 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [4.5.2 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)
