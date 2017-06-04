---
title: "部分信頼コードからのライブラリの使用 | Microsoft Docs"
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
  - "AllowPartiallyTrustedCallersAttribute 属性"
  - "APTCA"
  - "コード アクセス セキュリティ, 部分的に信頼されるコード"
  - "部分信頼"
  - "部分的に信頼されるコード"
  - "セキュリティ [.NET Framework], 部分的に信頼されるコード"
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
caps.latest.revision: 25
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 23
---
# 部分信頼コードからのライブラリの使用
> [!NOTE]
>  このトピックでは、厳密な名前を付けたアセンブリの動作について説明し、[レベル 1](../../../docs/framework/misc/security-transparent-code-level-1.md) のアセンブリにのみ適用します。[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降の[透過的セキュリティ コード、レベル 2](../../../docs/framework/misc/security-transparent-code-level-2.md) アセンブリは、厳密な名前の影響を受けません。 セキュリティ システムへの変更の詳細については、「[セキュリティの変更点](../../../docs/framework/security/security-changes.md)」を参照してください。  
  
> [!CAUTION]
>  コード アクセス セキュリティと部分的に信頼できるコード  
>   
>  .NET Framework には、コード アクセス セキュリティ \(CAS\) と呼ばれる、同一アプリケーションで実行される各種コードにさまざまな信頼レベルを強制的に適用するメカニズムが備わっています。  .NET Framework におけるコード アクセス セキュリティを、部分的に信頼できるコード、特に発生元の不明なコードのセキュリティ境界として使用しないでください。 発生元の不明なコードの読み込みと実行に関しては、他のセキュリティ対策を適切に導入することなく行わないようにしてください。  
>   
>  このポリシーは .NET Framework のすべてのバージョンに適用されますが、Silverlight に含まれる .NET Framework には適用されません。  
  
 ホストまたはサンドボックスから不完全な信頼を受けているアプリケーションは、ライブラリの作成者が <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性を使用して具体的に許可しない限り、共有マネージ ライブラリを呼び出せません。 そのため、アプリケーションの作成者は、ライブラリによっては部分的に信頼されたコンテキストから使用できないことを認識する必要があります。 既定では、部分的に信頼された[サンドボックス](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)で実行し、完全に信頼されたアセンブリの一覧にないコードはすべて、部分的に信頼されたコードです。 部分的に信頼されたコンテキストからコードを実行する、または部分的に信頼されたコードによってコードが呼び出されることはないと考えられる場合は、このセクションの情報を考慮する必要はありません。 ただし、部分的に信頼されたコードと対話する必要があるコード、または部分的に信頼されたコンテキストから操作するコードを記述する場合は、次の要因を考慮する必要があります。  
  
-   ライブラリは、複数のアプリケーションで共有するために、厳密な名前で署名する必要があります。 厳密な名前を使用すると、コードをグローバル アセンブリ キャッシュに配置したり、サンドボックス化する <xref:System.AppDomain> の完全信頼一覧に追加したりできます。また、コンシューマーは、実際にあなたが発信する特定のモバイル コードを確認することができます。  
  
-   既定では、厳密な名前[レベル 1](../../../docs/framework/misc/security-transparent-code-level-1.md) 共有ライブラリは、完全信頼のために暗黙的な [LinkDemand](../../../docs/framework/misc/link-demands.md) を実行します。ライブラリの作成者は何もする必要はありません。  
  
-   呼び出し元に完全な信頼がないにもかかわらず、このようなライブラリを呼び出そうとする場合、ランタイムは <xref:System.Security.SecurityException> をスローします。これにより、呼び出し元はライブラリにリンクできなくなります。  
  
-   自動の **LinkDemand** を無効にして例外がスローされないようにするために、**AllowPartiallyTrustedCallersAttribute** 属性を共有ライブラリのアセンブリのスコープに配置することができます。 この属性により、部分的に信頼されたマネージ コードからライブラリを呼び出すことができます。  
  
-   それでも、この属性を持つライブラリへのアクセスが許可されている部分的に信頼されたコードは、<xref:System.AppDomain> が定義する追加の制約を受けます。  
  
-   部分的に信頼されたコードが **AllowPartiallyTrustedCallersAttribute**  属性を持たないライブラリをプログラム上で呼び出す方法はありません。  
  
 特定のアプリケーションにとってプライベートなライブラリには、厳密な名前または**AllowPartiallyTrustedCallersAttribute** 属性は必要ありません。また、アプリケーションの外部にある潜在的に悪意のあるコードによって参照することはできません。 このようなコードは、部分的に信頼されたモバイル コードの意図的または意図的でない誤使用から保護されています。開発者は追加で何かをする必要はありません。  
  
 次の種類のコードについて、部分的に信頼されたコードによる使用を明示的に有効にすることを検討してください。  
  
-   セキュリティの脆弱性を入念にテストされ、「[安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)」に記載されたガイドラインに準拠しているコード。  
  
-   部分的に信頼されたシナリオ用に特に記述された厳密な名前のコード ライブラリ。  
  
-   インターネットからダウンロードしたコードによって呼び出される、厳密な名前で署名された \(部分的に信頼された、または完全に信頼された\) すべてのコンポーネント。  
  
> [!NOTE]
>  .NET Framework クラス ライブラリの一部のクラスは、**AllowPartiallyTrustedCallersAttribute** 属性がないため、部分的に信頼されたコードから呼び出すことはできません。  
  
## 参照  
 [コード アクセス セキュリティ](../../../docs/framework/misc/code-access-security.md)