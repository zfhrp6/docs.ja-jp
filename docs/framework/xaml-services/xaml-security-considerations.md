---
title: XAML セキュリティの考慮事項
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: ef47e7e370082a2050406710edcb62d0967df8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562363"
---
# <a name="xaml-security-considerations"></a>XAML セキュリティの考慮事項
このトピックは、XAML と .NET Framework XAML サービス API を使用するときに、アプリケーションのセキュリティのベスト プラクティスを説明します。  
  
## <a name="untrusted-xaml-in-applications"></a>アプリケーションで信頼されていない XAML  
 最も一般的な意味では、信頼されていない XAML は、アプリケーションの表示または出力しなかった以外にインクルードするすべての XAML ソースです。  
  
 XAML にコンパイルまたはとして格納されている、 `resx`-信頼されたおよび署名されたアセンブリ内で型のリソースが本質的に信頼されていません。 全体として、アセンブリを信頼する限り、XAML を信頼できます。 ほとんどの場合、ストリームまたはその他の I/O から読み込まれる XAML ソースでは、loose XAML の信頼の側面に関係するはのみです。 Loose XAML は、特定のコンポーネントまたは配置とパッケージ化インフラストラクチャを持つアプリケーション モデルの機能ではありません。 ただし、アセンブリは、loose XAML を読み込む必要がある動作を実装する場合があります。  
  
 、信頼されていない xaml にする必要があります扱う一般に、同じ信頼できないコードの場合と同様。 サンド ボックスまたは他の要素を使用して、信頼されるコードにアクセスできなくなる可能性のある信頼されていない XAML にします。  
  
 XAML 機能の性質は、XAML オブジェクトを構築し、それらのプロパティを設定する権利を与えます。 型コンバーター、マッピング、およびマークアップ拡張機能を使用して、アプリケーション ドメインでアセンブリへのアクセスにアクセスするこれらの機能も含める`x:Code`ブロック、およびなどです。  
  
 そのレベルの言語機能だけでなく XAML は、多くのテクノロジの UI の定義に使用されます。 信頼されていない XAML を読み込むには、悪意のあるスプーフィング UI を読み込む可能性があります。  
  
## <a name="sharing-context-between-readers-and-writers"></a>リーダーとライターの間でコンテキストを共有  
 .NET Framework XAML サービス アーキテクチャは、XAML リーダーと XAML ライターでは、多くの場合、XAML ライターまたは XAML スキーマ コンテキストを共有するための XAML リーダーの共有が必要です。 XAML ノード ループのロジックを作成しているか、パスを保存するカスタムを提供する場合、オブジェクトまたはコンテキストの共有が必要があります。 XAML リーダーのインスタンス、既定以外の XAML スキーマ コンテキスト、または信頼されていると信頼されていないコードの間での XAML リーダー/ライター クラスの設定を共有しないでください。  
  
 ほとんどのシナリオと XAML オブジェクトのバッキング CLR ベースの型の記述に関連する操作では、既定の XAML スキーマ コンテキストだけを使用できます。 既定の XAML スキーマ コンテキストは、完全な信頼を損なうおそれのある設定を明示的には含まれません。 安全に信頼されたコンポーネントと信頼されていない XAML リーダー/ライター コンポーネント間でコンテキストを共有は、です。 ただし、これを行うことがあるこのようなリーダーおよびライターを個別に保持することをお勧め<xref:System.AppDomain>具体的には意図したものとサンド ボックス化された部分信頼のうちの 1 つのスコープです。  
  
## <a name="xaml-namespaces-and-assembly-trust"></a>XAML 名前空間とアセンブリの信頼レベル  
 基本的な構文が不適切な XAML がアセンブリにカスタム XAML 名前空間のマッピングを解釈する方法の定義は区別されません、アプリケーション ドメインに読み込まれた、信頼できる、信頼されていないアセンブリです。 したがって、信頼されたアセンブリの目的の XAML 名前空間マッピングを偽装し、XAML ソースの宣言されたオブジェクトとプロパティの情報をキャプチャする信頼されていないアセンブリの技術的に可能なは。 このような状況を回避するためのセキュリティ要件がある場合は、目的の XAML 名前空間のマッピングにするかどうを使用して、次の手法のいずれか。  
  
-   アプリケーションの XAML によって行われたすべての XAML 名前空間マッピングで厳密な名前でアセンブリの完全修飾名を使用します。  
  
-   アセンブリの特定を構築することによって、参照アセンブリの固定セットへのマッピングを制限する<xref:System.Xaml.XamlSchemaContext>XAML リーダーと XAML オブジェクト ライター。 「<xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>」を参照してください。  
  
## <a name="xaml-type-mapping-and-type-system-access"></a>XAML の型マッピングおよびシステム アクセスの種類  
 XAML では、独自の型システムがあるさまざまな方法でピア CLR が、基本的な CLR 型システムを実装する方法をサポートしています。 ただし、特定の要素の型情報に基づいて、型に関する信頼の決定を行う型対応の型のバッキング CLR の型情報に従う必要があります。 これは XAML 型システムの特定のレポート機能の一部は仮想メソッドとして開かれたままを完全に元の .NET Framework XAML サービス実装の制御下です。 これらの拡張ポイントは、XAML 型システムでは、拡張可能な XAML 自体の拡張機能とその考えられる別型マッピングの手法と、既定の実装で CLR バックアップおよび既定の XAML スキーマ コンテキストとを照合するために存在します。 詳細については、のプロパティのいくつかの特定のノートを参照してください。<xref:System.Xaml.XamlType>と<xref:System.Xaml.XamlMember>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xaml.Permissions.XamlAccessLevel>
