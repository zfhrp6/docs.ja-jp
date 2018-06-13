---
title: 依存関係プロパティのセキュリティ
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers [WPF], access
- wrappers [WPF], security
- dependency properties [WPF], security
- security [WPF], wrappers
- validation [WPF], dependency properties
- dependency properties [WPF], access
- security [WPF], dependency properties
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
ms.openlocfilehash: 825b2a3dc79300f0cc26514398b8de0abee64fd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540505"
---
# <a name="dependency-property-security"></a>依存関係プロパティのセキュリティ
依存関係プロパティは、一般に、パブリック プロパティと考える必要があります。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のプロパティ システムの性質のため、依存関係プロパティの値に関してセキュリティを保証することはできません。  
  
  
<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>ラッパーと依存関係プロパティのアクセスとセキュリティ  
 通常、依存関係プロパティは、インスタンスからのプロパティの取得または設定を簡素化する "ラッパー" [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] プロパティと共に実装されます。 ただし、ラッパーは、基になるを実装するだけの便利なメソッド<xref:System.Windows.DependencyObject.GetValue%2A>と<xref:System.Windows.DependencyObject.SetValue%2A>依存関係プロパティを扱うときに使用される静的な呼び出しです。 別の考え方をすれば、プロパティは、プライベート フィールドではなくたまたま依存関係プロパティが基になっている [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] プロパティとして公開されます。 ラッパーに適用されるセキュリティ メカニズムでは、プロパティ システムの動作と基になっている依存関係プロパティのアクセスは並列化されません。 ラッパーのセキュリティ確認要求を配置することは便利なメソッドの使用状況を防ぐだけがへの呼び出しを防ぐことはできません<xref:System.Windows.DependencyObject.GetValue%2A>または<xref:System.Windows.DependencyObject.SetValue%2A>です。 同様に、保護されたアクセス レベルまたはプライベート アクセス レベルをラッパーに適用しても、効果的なセキュリティは提供されません。  
  
 独自の依存関係プロパティを記述する場合は、ラッパーを宣言する必要があります、<xref:System.Windows.DependencyProperty>できるように、呼び出し元はいない取得は誤解を招くそのプロパティの場合は true アクセス レベルに関する情報 (そのストア中のために、識別子が、パブリック メンバーとしてフィールド。実装される依存関係プロパティとして)。  
  
 カスタム依存関係プロパティの読み取り専用の依存関係プロパティとして、プロパティを登録することができ、これはへの参照を保持していないすべてのユーザーが設定されているプロパティを回避するという効果的な手段を提供、<xref:System.Windows.DependencyPropertyKey>プロパティです。 詳細については、「[読み取り専用の依存関係プロパティ](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)」を参照してください。  
  
> [!NOTE]
>  宣言、<xref:System.Windows.DependencyProperty>識別子フィールド プライベートが許可されていません、およびカスタム クラスの直後に公開されている名前空間を減らすためにも使用できますが、このようなプロパティと見なすことと同じ意味で"private"、 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]言語の定義は、次のセクションで説明されているため、アクセス レベルを定義します。  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>プロパティ システムによる依存関係プロパティの公開  
 一般的に効果的ではなく、宣言する誤解が生じる可能性が、<xref:System.Windows.DependencyProperty>パブリック以外の場合、すべてのアクセス レベルします。 このようなアクセス レベルの設定は、宣言しているクラスからインスタンスへの参照を取得できるのを防ぐだけです。 返すプロパティ システムのいくつかの要素がありますが、<xref:System.Windows.DependencyProperty>クラスのインスタンスまたは派生クラスのインスタンス上に存在して、この識別子で引き続き使用できるように、特定のプロパティを識別するための手段として、<xref:System.Windows.DependencyObject.SetValue%2A>も呼び出す場合は、元の静的な識別子は非公開として宣言されます。 また、<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>仮想メソッドが値を変更する既存の依存関係プロパティの情報を受信します。 さらに、<xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A>メソッドは、ローカルで設定を持つインスタンスで任意のプロパティの識別子を返しますの値。  
  
### <a name="validation-and-security"></a>検証とセキュリティ  
 要求を適用する、<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>と適切なセキュリティ メカニズムをなってをプロパティが設定されていることを防ぐために必要に応じてエラーの発生時に検証エラーを指定してください。 によって値の設定の無効化が強制実行<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>それらの呼び出し元は、アプリケーション ドメイン内で動作している場合、悪意のある呼び出し元が抑制も可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
