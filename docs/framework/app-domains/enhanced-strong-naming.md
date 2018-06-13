---
title: 拡張された厳密な名前付け
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf4a8df87cd507f2bfb17086e83dc8374a22fe71
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746892"
---
# <a name="enhanced-strong-naming"></a>拡張された厳密な名前付け
厳密な名前の署名は、アセンブリを識別するための .NET Framework の識別機構です。 これは通常、発行元 (署名者) から受取人 (検証者) に対して渡されるデータの整合性を検証するために使用される、公開キーによるデジタル署名です。 この署名はアセンブリに対する一意の ID として使用され、これによりアセンブリへの参照のあいまいさをなくします。 アセンブリはビルド プロセスの一部として署名され、読み込まれるときに検証されます。  
  
 厳密な名前の署名により、悪意のあるユーザーがアセンブリを不正に変更して、元の署名者のキーでアセンブリを再署名することを防ぐことができます。 ただし、厳密な名前キーには、発行者に関する信頼できる情報も、証明書の階層構造も含まれていません。 厳密な名前の署名は、アセンブリの署名者の信頼性を保証するものではなく、またその署名者がキーの正当な所有者であることを示すものでもありません。厳密な名前の署名は、キーの所有者がアセンブリに署名したことのみを示しています。 したがって、信頼できるサードパーティのコードのためのセキュリティの検証コントロールとして、厳密な名前の署名を使用することはお勧めしません。 コードを認証するために推奨される方法は、Microsoft Authenticode です。  
  
## <a name="limitations-of-conventional-strong-names"></a>従来の厳密な名前の制限  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以前のバージョンで使用されている厳密な名前付けのテクノロジには次の欠点があります。  
  
-   キーが常に攻撃を受ける状態に置かれています。テクノロジとハードウェアの向上により、公開キーから秘密キーを推測することが容易になっています。 攻撃からの保護には、より大きなキーが必要です。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] より前のバージョンでは任意のサイズのキー (既定のサイズは 1024 ビット) で署名する機能を提供していますが、新しいキーでアセンブリを署名すると、アセンブリの古い ID を参照しているすべてのバイナリが動作しなくなります。 したがって、互換性を維持する場合には、署名キーのサイズの更新は非常に困難です。  
  
-   厳密な名前の署名は SHA-1 アルゴリズムのみをサポートします。 SHA-1 は、最近、セキュリティが強化されたハッシュ アプリケーションのためには不十分であることがわかりました。 したがって、より強力なアルゴリズム (SHA-256 以上) が必要です。 SHA-1 は FIPS 準拠の地位を失う可能性があり、これによって FIPS 準拠のソフトウェアとアルゴリズムのみを選択して使用しているユーザーには問題が生じることになります。  
  
## <a name="advantages-of-enhanced-strong-names"></a>強化された厳密な名前の利点  
 強化された厳密な名前の主な利点は、既存の厳密な名前との互換性と、ある ID が別の ID と等価であることを指定できる機能です。  
  
-   既存の署名付きアセンブリを持つ開発者は、以前の ID を参照するアセンブリとの互換性を保ちながら、それらのアセンブリの ID を SHA-2 アルゴリズムに移行できます。  
  
-   新しいアセンブリを作成する際に、既存の厳密な名前の署名を考慮する必要のない開発者は、より安全な SHA-2 アルゴリズムを使用して、今までどおりにアセンブリに署名できます。  
  
## <a name="using-enhanced-strong-names"></a>強化された厳密な名前の使用  
 厳密な名前のキーは署名キーと ID のキーで構成されます。 アセンブリは署名キーで署名され、ID キーで識別されます。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] より前では、これらの 2 つのキーは同一です。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、ID キーは、.NET Framework の以前のバージョンと同じですが、署名キーは、より強力なハッシュ アルゴリズムを備えています。 さらに、副署名を作成するために、署名キーは ID キーで署名されます。  
  
 <xref:System.Reflection.AssemblySignatureKeyAttribute> 属性によって、アセンブリのメタデータはアセンブリの ID に既存の公開キーを使用することができ、これによって、古いアセンブリ参照は引き続き動作します。  <xref:System.Reflection.AssemblySignatureKeyAttribute> の属性は副署名を使用して、新しい署名キーの所有者が古い ID キーの所有者にもなるようにします。  
  
### <a name="signing-with-sha-2-without-key-migration"></a>キー移行を伴わない SHA-2 による署名  
 厳密な名前の署名を移行せずにアセンブリに署名するには、コマンド プロンプト ウィンドウから次のコマンドを実行します。  
  
1.  新しい ID キーを生成します (必要な場合)。  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  ID の公開キーを抽出し、このキーで署名する場合に SHA-2 アルゴリズムを使用するように指定します。  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  ID 公開キー ファイルで、アセンブリに遅延署名します。  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  完全な ID キーのペアでアセンブリに再署名します。  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a>キー移行を伴う SHA-2 による署名  
 移行した厳密な名前の署名でアセンブリに署名するには、コマンド プロンプト ウィンドウで次のコマンドを実行します。  
  
1.  ID キーと署名キーのペアを生成します (必要な場合)。  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  署名の公開キーを抽出し、このキーで署名する場合に SHA-2 アルゴリズムを使用するように指定します。  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  副署名を生成するハッシュ アルゴリズムを決定する ID の公開キーを抽出します。  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  <xref:System.Reflection.AssemblySignatureKeyAttribute> の属性のパラメーターを生成し、アセンブリに属性を追加します。  
  
    ```  
    sn -ac IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  
  
5.  ID 公開キーでアセンブリに遅延署名します。  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  完全な署名キーのペアでアセンブリに署名します。  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>参照  
 [厳密な名前付きアセンブリの作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
