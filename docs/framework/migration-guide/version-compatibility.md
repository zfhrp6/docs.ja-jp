---
title: ".NET Framework のバージョンの互換性"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework 4.5, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 166d61339d2b74f378b50ade4b78fd41e9692f76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
  
 この制限のため、互換性の保証は、コンポーネントにとって特に重要です。 .NET Framework 4 以降、コンポーネントに <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> 属性を適用することにより、複数のバージョンで想定されるコンポーネントの互換性の程度を指定できるようになりました。 ツールは、この属性を使用して、コンポーネントの将来のバージョンでの互換性保証の潜在的な違反を検出できます。  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a>下位互換性と .NET Framework 4.5  
 .NET Framework 4.5 およびそれ以降のバージョンは、旧バージョンと互換性のある以前のバージョンの .NET Framework でビルドされたアプリを使用しています。 つまり、アプリと以前のバージョンでビルドされたコンポーネントは動作変更しなくても、.NET Framework 4.5 とそれ以降のバージョンにします。 ただし、既定では、アプリ実行対象の開発に、共通言語ランタイムのバージョンのため、.NET Framework 4.5 またはそれ以降のバージョンで実行するアプリを有効にする構成ファイルを提供する必要があります。 詳細については、この記事の前半に記載した「[アプリのバージョンの互換性](#Apps)」を参照してください。  
  
 現実的には、この互換性は、.NET Framework のわずかな変更やプログラミング技法の変化によって損なわれている可能性があります。 たとえば、.NET Framework 4.5 でのパフォーマンスの向上によって、旧バージョンでは発生しなかった競合状態が顕在化する可能性があります。 同様に、.NET Framework アセンブリへのハードコーディングされたパスの使用、.NET Framework の特定のバージョンでの等値比較の実行、およびリフレクションの使用によるプライベート フィールドの値の取得は、下位互換性のない動作です。 さらに、各バージョンの .NET Framework には、バグの修正とセキュリティに関連する変更が含まれており、これらが一部のアプリとコンポーネントの互換性に影響する可能性があります。  
  
 アプリまたはコンポーネントが機能しない場合、.NET Framework 4.5 で期待どおりに (そのポイント リリースを含む、 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]4.5.2、4.6、4.6.1、4.6.2、4.7、または 4.7.1 は、次のチェックリストを使用します。  
  
-  場合は、アプリが .NET Framework 4.0 以降、.NET Framework のすべてのバージョンで実行しを参照してくださいに開発された[、.NET Framework アプリケーションの互換性](application-compatibility.md)を対象となる .NET Framework のバージョン間の変更の一覧を生成するにはアプリが実行されているバージョン。  

- .NET Framework 3.5 アプリがある場合も表示[.NET Framework 4 の移行に関する問題](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)です。

- .NET Framework 2.0 アプリケーションがある場合も表示[.NET Framework 3.5 SP1 の変更](http://go.microsoft.com/fwlink/?LinkId=186989)です。

- .NET Framework 1.1 アプリがある場合も表示[.NET Framework 2.0 で変更](http://go.microsoft.com/fwlink/?LinkID=125263)です。  
  
-   を実行する .NET Framework 4.5 またはそのポイント リリースでは、既存のソース コードを再コンパイルする場合、または、アプリまたはコンポーネントを対象とするの新しいバージョンを開発している場合、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]またはそのポイントは、既存のソース コード ベース、チェックからリリース[クラス ライブラリに残されている機能](../../../docs/framework/whats-new/whats-obsolete.md)旧式の型およびメンバー、および説明されている回避策を適用します。 (コンパイル済みのコードは、互換性のために残されている旧式の型とメンバーに対して引き続き実行されます)。  
  
-   アプリが正常に動作しない原因が [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] での変更によるものとわかった場合は、「[ランタイム設定スキーマ](../../../docs/framework/configure-apps/file-schema/runtime/index.md)」を参照して、アプリの構成ファイルのランタイム設定を使用して以前の動作を復元できるかどうかを確認してください。  
  
-   説明されていない問題が発生した場合は、[Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=154815) にバグを報告し、[netfxcf@microsoft.com](mailto:netfxcf@microsoft.com) にバグ番号を連絡してください。  
  
## <a name="compatibility-and-side-by-side-execution"></a>互換性と side-by-side 実行  
 問題の適切な解決策が見つからない場合は、.NET Framework 4.5 (またはそのポイント リリース) は Version 1.1、2.0、3.5 と side-by-side で実行でき、Version 4 に置き換わるインプレース更新であることを思い出してください。 Version 1.1、2.0、3.5 を対象とするアプリでは、適切なバージョンの .NET Framework を対象コンピューターにインストールして、アプリを最良の環境で実行できます。 side-by-side 実行について詳しくは、[side-by-side 実行](../../../docs/framework/deployment/side-by-side-execution.md)に関するページを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [新機能](../../../docs/framework/whats-new/index.md)  
 [クラス ライブラリの互換性のために残されている機能](../../../docs/framework/whats-new/whats-obsolete.md)  
 [アプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility.md)  
 [Microsoft .NET Framework のサポート ライフサイクル ポリシー](http://go.microsoft.com/fwlink/p/?LinkId=248212)  
 [.NET framework 4 への移行に関する問題](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)
