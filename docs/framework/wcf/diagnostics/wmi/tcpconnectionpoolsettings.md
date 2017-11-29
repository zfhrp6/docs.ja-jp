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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5038d093333eca9ca191c3ecae4cfa889d723276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="79e14-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="79e14-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="79e14-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="79e14-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79e14-104">構文</span><span class="sxs-lookup"><span data-stu-id="79e14-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="79e14-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="79e14-105">Methods</span></span>  
 <span data-ttu-id="79e14-106">TcpConnectionPoolSettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="79e14-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="79e14-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="79e14-107">Properties</span></span>  
 <span data-ttu-id="79e14-108">TcpConnectionPoolSettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="79e14-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="79e14-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="79e14-109">GroupName</span></span>  
 <span data-ttu-id="79e14-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="79e14-110">Data type: string</span></span>  
  
 <span data-ttu-id="79e14-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="79e14-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79e14-112">バインド要素により使用される接続プールのグループ名。</span><span class="sxs-lookup"><span data-stu-id="79e14-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="79e14-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="79e14-113">IdleTimeout</span></span>  
 <span data-ttu-id="79e14-114">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="79e14-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="79e14-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="79e14-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79e14-116">接続が切断されるまでの最大アイドル時間。</span><span class="sxs-lookup"><span data-stu-id="79e14-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="79e14-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="79e14-117">LeaseTimeout</span></span>  
 <span data-ttu-id="79e14-118">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="79e14-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="79e14-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="79e14-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79e14-120">リース操作を完了する必要がある、タイムアウトまでの最大時間。</span><span class="sxs-lookup"><span data-stu-id="79e14-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="79e14-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="79e14-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="79e14-122">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="79e14-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="79e14-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="79e14-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79e14-124">各エンドポイントの発信接続の最大数。</span><span class="sxs-lookup"><span data-stu-id="79e14-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79e14-125">要件</span><span class="sxs-lookup"><span data-stu-id="79e14-125">Requirements</span></span>  
  
|<span data-ttu-id="79e14-126">MOF</span><span class="sxs-lookup"><span data-stu-id="79e14-126">MOF</span></span>|<span data-ttu-id="79e14-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="79e14-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="79e14-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="79e14-128">Namespace</span></span>|<span data-ttu-id="79e14-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="79e14-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79e14-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="79e14-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
