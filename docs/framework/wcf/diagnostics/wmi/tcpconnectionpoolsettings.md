---
title: TcpConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04e6a457a9f4c3f93a52f851aafe70578b7d7444
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="28540-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="28540-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="28540-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="28540-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28540-104">構文</span><span class="sxs-lookup"><span data-stu-id="28540-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="28540-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="28540-105">Methods</span></span>  
 <span data-ttu-id="28540-106">TcpConnectionPoolSettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="28540-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="28540-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="28540-107">Properties</span></span>  
 <span data-ttu-id="28540-108">TcpConnectionPoolSettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="28540-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="28540-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="28540-109">GroupName</span></span>  
 <span data-ttu-id="28540-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="28540-110">Data type: string</span></span>  
  
 <span data-ttu-id="28540-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="28540-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28540-112">バインド要素により使用される接続プールのグループ名。</span><span class="sxs-lookup"><span data-stu-id="28540-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="28540-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="28540-113">IdleTimeout</span></span>  
 <span data-ttu-id="28540-114">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="28540-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="28540-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="28540-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28540-116">接続が切断されるまでの最大アイドル時間。</span><span class="sxs-lookup"><span data-stu-id="28540-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="28540-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="28540-117">LeaseTimeout</span></span>  
 <span data-ttu-id="28540-118">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="28540-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="28540-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="28540-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28540-120">リース操作を完了する必要がある、タイムアウトまでの最大時間。</span><span class="sxs-lookup"><span data-stu-id="28540-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="28540-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="28540-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="28540-122">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="28540-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="28540-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="28540-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28540-124">各エンドポイントの発信接続の最大数。</span><span class="sxs-lookup"><span data-stu-id="28540-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28540-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="28540-125">Requirements</span></span>  
  
|<span data-ttu-id="28540-126">MOF</span><span class="sxs-lookup"><span data-stu-id="28540-126">MOF</span></span>|<span data-ttu-id="28540-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="28540-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="28540-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="28540-128">Namespace</span></span>|<span data-ttu-id="28540-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="28540-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28540-130">参照</span><span class="sxs-lookup"><span data-stu-id="28540-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
