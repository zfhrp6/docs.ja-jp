---
title: ".NET Framework のバージョンの互換性 | Microsoft Docs"
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
- .NET Framework, version compatibility
- .NET Framework 4.5, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
caps.latest.revision: 35
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 09f682d9c3a1cf5d42bba878676d84b9328a1a81
ms.lasthandoff: 04/18/2017

---
# <a name="version-compatibility-in-the-net-framework"></a>.NET Framework のバージョンの互換性
下位互換とは、プラットフォームの特定のバージョンで開発されたアプリが、そのプラットフォームの新しいバージョンでも実行できることを意味します。 .NET Framework では、下位互換性が最大限に高められています。.NET Framework のあるバージョンで記述されたソース コードは、.NET Framework の新しいバージョンでコンパイルでき、.NET Framework のあるバージョンで実行されるバイナリは、新しいバージョンの .NET Framework でも同じように動作します。  
  
<a name="Apps"></a>   
## <a name="version-compatibility-for-apps"></a>アプリのバージョンの互換性  
 既定では、アプリは、ビルド対象の .NET Framework のバージョンで実行されます。 そのバージョンが存在せず、アプリの構成ファイルにサポートされるバージョンが定義されていない場合は、.NET Framework 初期化エラーが発生することがあります。 この場合、アプリは実行できません。  
  
 アプリを実行する特定のバージョンを定義するには、1 つ以上の [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 要素をアプリの構成ファイルに追加します。 各 `<supportedRuntime>` 要素は、サポートされるランタイムのバージョンを示します。最初の要素で最も優先度の高いバージョンを、最後の要素で最も優先度の低いバージョンを指定します。  
  
```xml  
  
<configuration>  
   <startup>  
      <supportedRuntime version="v2.0.50727" />  
      <supportedRuntime version="v4.0" />  
   </startup>  
</configuration>  
  
```  
  
 詳しくは、[.NET Framework 4 または 4.x をサポートするアプリの構成方法](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)に関するページをご覧ください。  
  
## <a name="version-compatibility-for-components"></a>コンポーネントのバージョンの互換性  
 アプリは、それが実行される .NET Framework を制御できますが、コンポーネントは制御できません。 コンポーネントとクラス ライブラリは特定のアプリのコンテキストで読み込まれるので、アプリが実行されるバージョンの .NET Framework で自動的に実行されます。  
  
 この制限のため、互換性の保証は、コンポーネントにとって特に重要です。 .NET Framework 4 以降では、コンポーネントに <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=fullName> 属性を適用することにより、複数のバージョン間で許可されるコンポーネントの互換性を指定できるようになりました。 ツールは、この属性を使用して、コンポーネントの将来のバージョンでの互換性保証の潜在的な違反を検出できます。  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a>下位互換性と .NET Framework 4.5  
 .NET Framework 4.5 およびそのポイント リリース (4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7) には、以前のバージョンの .NET Framework でビルドされたアプリと下位互換性があります。 つまり、旧バージョンの .NET Framework でビルドしたアプリとコンポーネントは、.NET Framework 4.5 で変更を行わずに動作します。 ただし、既定では、アプリは、開発された共通言語ランタイムのバージョンで動作するため、アプリを .NET Framework 4.5 で実行するには構成ファイルを提供する必要がある場合があります。 詳細については、この記事の前半に記載した「[アプリのバージョンの互換性](#Apps)」を参照してください。  
  
 現実的には、この互換性は、.NET Framework のわずかな変更やプログラミング技法の変化によって損なわれている可能性があります。 たとえば、.NET Framework 4.5 でのパフォーマンスの向上によって、旧バージョンでは発生しなかった競合状態が顕在化する可能性があります。 同様に、.NET Framework アセンブリへのハードコーディングされたパスの使用、.NET Framework の特定のバージョンでの等値比較の実行、およびリフレクションの使用によるプライベート フィールドの値の取得は、下位互換性のない動作です。 さらに、各バージョンの .NET Framework には、バグの修正とセキュリティに関連する変更が含まれており、これらが一部のアプリとコンポーネントの互換性に影響する可能性があります。  
  
 アプリまたはコンポーネントが .NET Framework 4.5 (ポイント リリースである [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]、4.5.2、4.6、4.6.1、4.6.2、4.7 を含む) で期待どおりに動作しない場合は、次のチェックリストを参考にしてください。  
  
-   これらのトピックで、アプリに影響する可能性がある変更を確認し、説明されている代替手段を適用します。  
  
    -   [.NET framework 4 への移行に関する問題](http://go.microsoft.com/fwlink/p/?LinkId=248212)  
  
    -   [4.5 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)  
  
    -   [4.5.1 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)  
  
    -   [4.5.2 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)  
  
    -   [4.6 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6.md)  
  
    -   [4.6.1 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)  
  
    -   [4.6.2 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)  

    - [4.7 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
       
-   .NET Framework 1.1 アプリがある場合は、次のトピックもレビューしてください。  
  
    -   [.NET Framework 2.0 の互換性に影響する変更点](http://go.microsoft.com/fwlink/?LinkID=125263)  
  
    -   [.NET Framework 3.5 SP1 の変更点](http://go.microsoft.com/fwlink/?LinkId=186989)  
  
-   .NET Framework 4.5 またはそのポイント リリースで実行するために既存のソース コードを再コンパイルする場合、または [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] をターゲットとするアプリまたはコンポーネントの新しいバージョンを既存のソース コード ベースから開発する場合は、[クラス ライブラリの互換性のために残されている機能](../../../docs/framework/whats-new/whats-obsolete.md)に関するページで廃止された型とメンバーを確認し、説明されている回避策を適用してください。 (コンパイル済みのコードは、互換性のために残されている旧式の型とメンバーに対して引き続き実行されます)。  
  
-   アプリが正常に動作しない原因が [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] での変更によるものとわかった場合は、「[ランタイム設定スキーマ](../../../docs/framework/configure-apps/file-schema/runtime/index.md)」を参照して、アプリの構成ファイルのランタイム設定を使用して以前の動作を復元できるかどうかを確認してください。  
  
-   説明されていない問題が発生した場合は、[Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=154815) にバグを報告し、[netfxcf@microsoft.com](mailto:netfxcf@microsoft.com) にバグ番号を連絡してください。  
  
## <a name="compatibility-and-side-by-side-execution"></a>互換性と side-by-side 実行  
 問題の適切な解決策が見つからない場合は、.NET Framework 4.5 (またはそのポイント リリース) は Version 1.1、2.0、3.5 と side-by-side で実行でき、Version 4 に置き換わるインプレース更新であることを思い出してください。 Version 1.1、2.0、3.5 を対象とするアプリでは、適切なバージョンの .NET Framework を対象コンピューターにインストールして、アプリを最良の環境で実行できます。 side-by-side 実行について詳しくは、[side-by-side 実行](../../../docs/framework/deployment/side-by-side-execution.md)に関するページを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [新機能](../../../docs/framework/whats-new/index.md)   
 [クラス ライブラリの互換性のために残されている機能](../../../docs/framework/whats-new/whats-obsolete.md)   
 [アプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility.md)   
 [Microsoft .NET Framework のサポート ライフサイクル ポリシー](http://go.microsoft.com/fwlink/p/?LinkId=248212)   
 [.NET framework 4 への移行に関する問題](http://go.microsoft.com/fwlink/p/?LinkId=248212)
