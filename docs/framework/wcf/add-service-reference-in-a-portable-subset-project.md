---
title: ポータブル サブセット プロジェクトでサービス参照を追加する
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: 5d094bb1d2d1155565e48850a2f41829a93cff84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="d1d48-102">ポータブル サブセット プロジェクトでサービス参照を追加する</span><span class="sxs-lookup"><span data-stu-id="d1d48-102">Add Service Reference in a Portable Subset Project</span></span>
<span data-ttu-id="d1d48-103">ポータブル サブセット プロジェクトは、.NET アセンブリ プログラマは 1 つのソース ツリーを保持し、複数の .NET 実装 (デスクトップ、Silverlight、Windows Phone、および XBOX) をサポートしながらビルド システムを有効にします。</span><span class="sxs-lookup"><span data-stu-id="d1d48-103">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and XBOX).</span></span> <span data-ttu-id="d1d48-104">ポータブル サブセット プロジェクトは、任意の .NET 実装で使用できる .NET framework アセンブリである .NET ポータブル ライブラリのみを参照します。</span><span class="sxs-lookup"><span data-stu-id="d1d48-104">Portable subset projects only reference .NET portable libraries which are a .NET framework assembly that can be used on any .NET implementation.</span></span>  
  
## <a name="add-service-reference-details"></a><span data-ttu-id="d1d48-105">サービス参照の追加の詳細</span><span class="sxs-lookup"><span data-stu-id="d1d48-105">Add Service Reference Details</span></span>  
 <span data-ttu-id="d1d48-106">ポータブル サブセット プロジェクトでサービス参照を追加する場合は、次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="d1d48-106">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1.  <span data-ttu-id="d1d48-107"><xref:System.Xml.Serialization.XmlSerializer> では、文字エンコーディングのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d1d48-107">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="d1d48-108">SOAP エンコーディングを使用すると、インポート中にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d1d48-108">SOAP encodings generate an error during import.</span></span>  
  
2.  <span data-ttu-id="d1d48-109"><xref:System.Runtime.Serialization.DataContractSerializer> シナリオを使用するサービスの場合、再利用された型をポータブル サブセットからのみ受け取ることを確認するために、データ コントラクト サロゲートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="d1d48-109">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3.  <span data-ttu-id="d1d48-110">ポータブル ライブラリでサポートされていないバインド (<xref:System.ServiceModel.BasicHttpBinding>、トランザクション フロー、信頼できるセッション、または MTOM エンコーディングがない <xref:System.ServiceModel.WSHttpBinding>、および等価のカスタム バインドを除くすべてのバインド) に依存するエンドポイントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="d1d48-110">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4.  <span data-ttu-id="d1d48-111">メッセージ ヘッダーは、インポート前にすべての操作におけるすべてのメッセージの説明から削除されます。</span><span class="sxs-lookup"><span data-stu-id="d1d48-111">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5.  <span data-ttu-id="d1d48-112">非ポータブル属性 (<xref:System.ComponentModel.DesignerCategoryAttribute>、<xref:System.SerializableAttribute>、および <xref:System.ServiceModel.TransactionFlowAttribute>) は、生成されたクライアント プロキシ コードから削除されます。</span><span class="sxs-lookup"><span data-stu-id="d1d48-112">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6.  <span data-ttu-id="d1d48-113">非ポータブル プロパティ (ProtectionLevel、SessionMode、IsInitiating、IsTerminating) は、<xref:System.ServiceModel.ServiceContractAttribute>、<xref:System.ServiceModel.OperationContractAttribute>、および <xref:System.ServiceModel.FaultContractAttribute> から削除されます。</span><span class="sxs-lookup"><span data-stu-id="d1d48-113">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7.  <span data-ttu-id="d1d48-114">すべてのサービス操作は、クライアント プロキシ上で非同期操作として生成されます。</span><span class="sxs-lookup"><span data-stu-id="d1d48-114">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8.  <span data-ttu-id="d1d48-115">非ポータブル型を使用する生成済みのクライアント コンストラクターは削除されます。</span><span class="sxs-lookup"><span data-stu-id="d1d48-115">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="d1d48-116"><xref:System.Net.CookieContainer> インスタンスは、生成されたクライアントで公開されます。</span><span class="sxs-lookup"><span data-stu-id="d1d48-116">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="d1d48-117">コード ジェネレーターのアセンブリとバージョンを示すコメント "`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`" がファイルの先頭に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="d1d48-117">A comment is inserted at the top of the file identifying the assembly and version of the code generator:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span></span>  
  
11. <span data-ttu-id="d1d48-118"><xref:System.Runtime.Serialization.ISerializable> インターフェイスはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d1d48-118">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="d1d48-119">Net.Tcp および PollingDuplex バインドはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d1d48-119">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="d1d48-120"><xref:System.Runtime.Serialization.DataContractSerializer> は常にエラーに対して使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1d48-120">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <span data-ttu-id="d1d48-121">ポータブル サブセット プロジェクトでは <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d1d48-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d48-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1d48-122">See Also</span></span>  
 [<span data-ttu-id="d1d48-123">WCF クライアントを使用したサービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="d1d48-123">Accessing Services Using a WCF Client</span></span>](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 <span data-ttu-id="d1d48-124">[ポータブル クラス ライブラリ](http://msdn.microsoft.com/library/gg597391\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d1d48-124">[Portable Class Library](http://msdn.microsoft.com/library/gg597391\(v=vs.110\))</span></span>
