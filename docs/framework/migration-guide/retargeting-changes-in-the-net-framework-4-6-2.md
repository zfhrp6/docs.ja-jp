---
title: ".NET Framework 4.6.2 における再ターゲットの変更点 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes, .NET Framework
- retargeting changes, .NET Framework 4.6.2
- application compatibility
ms.assetid: 76dc6849-8210-4e41-8731-20828c98b282
caps.latest.revision: 26
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 229ccf3fa4ff1029334641da350cfd040e4b286e
ms.lasthandoff: 04/18/2017

---
# <a name="retargeting-changes-in-the-net-framework-462"></a>.NET Framework 4.6.2 における再ターゲットの変更点
まれに、変更を再ターゲットすると [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象として再コンパイルされるアプリに影響する場合があります。 これらは、以前のバージョンの .NET Framework を対象とするバイナリには影響を与えませんが、バージョン 4.6.2 で実行されるバイナリには影響します。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] には、次の領域の変更の再ターゲットが含まれます。  
  
-   [コア](#Core)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows フォーム](#WinForms)  
  
 次の表の [スコープ] 列には、各変更の重要度を指定します。  
  
-   メジャー。 多数のアプリに影響するか、またはコードに大幅な変更が必要な、重大な変更。 変更の再ターゲットはこのカテゴリに分類されないことに注意してください。  
  
-   マイナー。 少数のアプリに影響するか、またはコードにわずかな変更が必要な、変更。  
  
-   エッジ。 一般的ではない特定のシナリオでアプリに影響を与える変更。  
  
-   透過。 アプリの開発者やユーザーには大きな影響を及ぼさない変更。 アプリはこの変更のために変更を加える必要はありません。  
  
<a name="Core"></a>   
## <a name="core"></a>コア  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|長いパスのサポート|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリ以降では、長いパス (最大 32,000 文字) がサポートされ、パスの長さにおける 260 文字 (または `MAX_PATH`) の制限はなくなりました。|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリの場合、以前に <xref:System.IO.PathTooLongException> をスローしたコードのパスは、例外をスローしなくなる可能性があります。 詳細については、「[軽減策: 長いパスのサポート](~/docs/framework/migration-guide/mitigation-long-path-support.md)」を参照してください。|Minor|  
|パスの正規化|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリ以降では、オペレーティング システムに従って、DOS デバイス パスへの優れたアクセスを提供するために、パスの正規化方法が変更されました。|この変更により、以前はサポートされていなかった有効なデバイス パスにアクセスできるようになります。 詳細については、「[軽減策: パスの正規化](~/docs/framework/migration-guide/mitigation-path-normalization.md)」を参照してください。|Minor|  
|<xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> および <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリ以降では、以前はサポートされていなかったパスをサポートするために (長さと形式の両方について) 数多くの変更が加えられました。 具体的には、適切なドライブの区切り構文 (コロン) のチェックがより正しく行われるようになりました。|これらの変更は、これらの 2 つのメソッドで以前はサポートされていた一部の URI のパスをブロックします。 詳細については、「[軽減策: パスのコロン チェック](~/docs/framework/migration-guide/mitigation-path-colon-checks.md)」を参照してください。|エッジ|  
|<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> コンストラクター|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降では、<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> メソッドの呼び出しで作成された <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> プロパティは、新しい <xref:System.Security.Claims.ClaimsIdentity> インスタンスになります。 以前のバージョンの .NET Framework では、<xref:System.Security.Claims.ClaimsIdentity.Actor%2A> は既存の参照です。|場合によっては、コンストラクターの <xref:System.Security.Principal.IIdentity> の <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> プロパティと <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> プロパティの比較では、異なる結果が返されます。<br /><br /> 詳細については、「[軽減策: ClaimsIdentity コンストラクター](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md)」を参照してください。|エッジ|  
|<xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor%2A?displayProperty=fullName>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリ以降では、<xref:System.Security.Cryptography.AesCryptoServiceProvider> 複合化で再利用可能な変換が提供されます。   <xref:System.Security.Cryptography.ICryptoTransform.TransformFinalBlock%2A> の呼び出しの後、変換は初期化し直され、再利用することができます。<br /><br /> 以前のバージョンの .NET Framework を対象とするアプリでは、<xref:System.Security.Cryptography.ICryptoTransform.TransformFinalBlock%2A> の呼び出しの後に、<xref:System.Security.Cryptography.ICryptoTransform.TransformBlock%2A> を呼び出して、複合化を再利用しようとすると、<xref:System.Security.Cryptography.CryptographicException> をスローするか、破損しているデータが生成されます。|これは例外の動作のため、影響は最小限にとどまります。<br /><br /> 前の動作に依存するアプリケーションは、そのアプリケーションの構成ファイルの [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して、この動作の使用を無効にすることができます。<br /><br /> `<runtime>    <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/> </runtime>`<br /><br /> また、以前のバージョンの .NET Framework を対象とするものの、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降のバージョンの .NET Framework で実行されているアプリでは、そのアプリケーションの構成ファイルの [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して、この動作を有効にできます。<br /><br /> `<runtime>    <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/> </runtime>`|Minor|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|CNG を使用して格納される証明書の WCF トランスポート セキュリティ サポート|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリ以降では、WCF トランスポート セキュリティでは、Windows 暗号化ライブラリ (CNG) を使用して格納される証明書がサポートされます。 このサポートは、指数の長さが 32 ビット以下の公開キーを持つ証明書に限定されます。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリケーションでは、この機能は既定で有効になります。<br /><br /> 以前のバージョンの .NET Framework では、CSG キー ストレージ プロバイダーによる X509 証明書を使用しようとすると、例外がスローされます。|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以前を対象とするものの、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] で実行されているアプリの場合、app.config または web.config ファイルのランタイム セクションに次の行を追加することで、CNG 証明書のサポートを有効にできます。<br /><br /> `<AppContextSwitchOverrides     value="Switch.System.ServiceModel.DisableCngCertificates=false" />`<br /><br /> 次のコードを使用してプログラムで行うこともできます。<br /><br /> `private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate"; AppContext.SetSwitch(disableCngCertificates, false);`<br /><br /> `Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates" AppContext.SetSwitch(disableCngCertificates, False)`<br /><br /> この変更のため、CNG 証明書の失敗で、セキュリティで保護された通信を開始する試行に依存する例外処理コードは、実行されなくなることに注意してください。|Minor|  
  
<a name="WinForms"></a>   
## <a name="windows-forms"></a>Windows フォーム  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName>、`System.ComponentModel.EventDescriptor.Equals`、および `System.ComponentModel.PropertyDescriptor.Equals`|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリ以降、基底クラスの <xref:System.ComponentModel.MemberDescriptor.Equals%2A> メソッドの実装が変更されました。|同じかどうかのテストは期待される結果を生成するようになったため、この変更による影響はほとんどありません。<br /><br /> ただし、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象としていて、前の動作に依存するアプリは、この変更を無効にできます。 同様に、以前のバージョンの .NET Framework を対象とするものの、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] で実行されているアプリは、この変更を有効にできます。 詳細については、「[軽減策: MemberDescriptor.Equals](~/docs/framework/migration-guide/mitigation-memberdescriptor-equals.md)」を参照してください。|エッジ|  
  
## <a name="see-also"></a>関連項目  
 [4.6.2 でのアプリケーションの互換性](~/docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
