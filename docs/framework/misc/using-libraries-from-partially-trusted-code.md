---
title: 部分信頼コードからのライブラリの使用
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b2eaf6ccebed38c778e328e34cb6f53177347b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397661"
---
# <a name="using-libraries-from-partially-trusted-code"></a>部分信頼コードからのライブラリの使用
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  このトピックではアセンブリの厳密な名前の動作に対処し、のみ適用されます[レベル 1](../../../docs/framework/misc/security-transparent-code-level-1.md)アセンブリ。 [セキュリティ透過的なコード、レベル 2](../../../docs/framework/misc/security-transparent-code-level-2.md)内のアセンブリ、[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]または後に影響ありません厳密な名前です。 セキュリティ システムへの変更の詳細については、次を参照してください。[セキュリティの変更点](../../../docs/framework/security/security-changes.md)です。  
  
 呼び出して、共有ホストまたはサンド ボックスから完全な信頼は許可されませんよりも小さいを受信するアプリケーション マネージ ライブラリ、ライブラリの作成者具体的に許可を使用しない限り、<xref:System.Security.AllowPartiallyTrustedCallersAttribute>属性。 そのため、アプリケーションの作成者は、ライブラリによっては部分的に信頼されたコンテキストから使用できないことを認識する必要があります。 既定では、すべてのコードを実行する部分信頼で[サンド ボックス](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)ではありません。 完全信頼アセンブリの一覧が部分的に信頼されているとします。 部分的に信頼されたコンテキストからコードを実行する、または部分的に信頼されたコードによってコードが呼び出されることはないと考えられる場合は、このセクションの情報を考慮する必要はありません。 ただし、部分的に信頼されたコードと対話する必要があるコード、または部分的に信頼されたコンテキストから操作するコードを記述する場合は、次の要因を考慮する必要があります。  
  
-   ライブラリは、複数のアプリケーションで共有するために、厳密な名前で署名する必要があります。 厳密な名前を使用すると、コードをグローバル アセンブリ キャッシュに配置したり、サンドボックス化する <xref:System.AppDomain> の完全信頼一覧に追加したりできます。また、コンシューマーは、実際にあなたが発信する特定のモバイル コードを確認することができます。  
  
-   既定では、厳密な名前[レベル 1](../../../docs/framework/misc/security-transparent-code-level-1.md)共有ライブラリを暗黙的な実行[LinkDemand](../../../docs/framework/misc/link-demands.md)完全信頼に自動的には、ライブラリの作成者が何もする必要なし。  
  
-   呼び出し元に完全な信頼がないにもかかわらず、このようなライブラリを呼び出そうとする場合、ランタイムは <xref:System.Security.SecurityException> をスローします。これにより、呼び出し元はライブラリにリンクできなくなります。  
  
-   自動を無効にするために**LinkDemand**と、例外がスローされないように、配置することができます、 **AllowPartiallyTrustedCallersAttribute**属性の共有アセンブリ スコープにライブラリです。 この属性により、部分的に信頼されたマネージ コードからライブラリを呼び出すことができます。  
  
-   それでも、この属性を持つライブラリへのアクセスが許可されている部分的に信頼されたコードは、<xref:System.AppDomain> が定義する追加の制約を受けます。  
  
-   プログラムによる方法部分的に信頼されたコードを持たないライブラリを呼び出すことはありません、 **AllowPartiallyTrustedCallersAttribute**属性。  
  
 特定のアプリケーションにとってプライベートなライブラリには、厳密な名前が不要または**AllowPartiallyTrustedCallersAttribute**属性し、アプリケーションの外部の悪意のあるコードによって参照することはできません。 このようなコードは、部分的に信頼されたモバイル コードの意図的または意図的でない誤使用から保護されています。開発者は追加で何かをする必要はありません。  
  
 次の種類のコードについて、部分的に信頼されたコードによる使用を明示的に有効にすることを検討してください。  
  
-   セキュリティの脆弱性を入念にテストされているし、で説明するガイドラインに準拠しているコード[安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)です。  
  
-   部分的に信頼されたシナリオ用に特に記述された厳密な名前のコード ライブラリ。  
  
-   インターネットからダウンロードしたコードによって呼び出される、厳密な名前で署名された (部分的に信頼された、または完全に信頼された) すべてのコンポーネント。   
  
> [!NOTE]
>  .NET Framework クラス ライブラリの一部のクラスはありません、 **AllowPartiallyTrustedCallersAttribute**属性で、部分的に信頼されたコードから呼び出すことはできません。  
  
## <a name="see-also"></a>関連項目  
 [コード アクセス セキュリティ](../../../docs/framework/misc/code-access-security.md)
