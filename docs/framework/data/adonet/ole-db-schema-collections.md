---
title: "OLE DB スキーマ コレクション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9b88308c5dad69ed1ba6f48f525931e94f13ef1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="0e7cd-102">OLE DB スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="0e7cd-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="0e7cd-103">ここでは、Microsoft SQL Server、Oracle、および Microsoft Jet 用の各 OLE DB プロバイダーでのスキーマ コレクションのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0e7cd-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="0e7cd-104">Microsoft SQL Server OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="0e7cd-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="0e7cd-105">Microsoft SQL Server OLE DB Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="0e7cd-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0e7cd-106">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="0e7cd-106">Tables</span></span>  
  
-   <span data-ttu-id="0e7cd-107">列</span><span class="sxs-lookup"><span data-stu-id="0e7cd-107">Columns</span></span>  
  
-   <span data-ttu-id="0e7cd-108">手順</span><span class="sxs-lookup"><span data-stu-id="0e7cd-108">Procedures</span></span>  
  
-   <span data-ttu-id="0e7cd-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0e7cd-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0e7cd-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="0e7cd-110">Catalog</span></span>  
  
-   <span data-ttu-id="0e7cd-111">Indexes</span><span class="sxs-lookup"><span data-stu-id="0e7cd-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0e7cd-112">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="0e7cd-112">Tables</span></span>  
  
|<span data-ttu-id="0e7cd-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-113">ColumnName</span></span>|<span data-ttu-id="0e7cd-114">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-115">TABLE_CATALOG</span></span>|<span data-ttu-id="0e7cd-116">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-116">String</span></span>|  
|<span data-ttu-id="0e7cd-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-118">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-118">String</span></span>|  
|<span data-ttu-id="0e7cd-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-119">TABLE_NAME</span></span>|<span data-ttu-id="0e7cd-120">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-120">String</span></span>|  
|<span data-ttu-id="0e7cd-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-121">TABLE_TYPE</span></span>|<span data-ttu-id="0e7cd-122">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-122">String</span></span>|  
|<span data-ttu-id="0e7cd-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-123">TABLE_GUID</span></span>|<span data-ttu-id="0e7cd-124">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-124">Guid</span></span>|  
|<span data-ttu-id="0e7cd-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-125">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-126">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-126">String</span></span>|  
|<span data-ttu-id="0e7cd-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-127">TABLE_PROPID</span></span>|<span data-ttu-id="0e7cd-128">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-128">Int64</span></span>|  
|<span data-ttu-id="0e7cd-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-129">DATE_CREATED</span></span>|<span data-ttu-id="0e7cd-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-130">DateTime</span></span>|  
|<span data-ttu-id="0e7cd-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-131">DATE_MODIFIED</span></span>|<span data-ttu-id="0e7cd-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0e7cd-133">列</span><span class="sxs-lookup"><span data-stu-id="0e7cd-133">Columns</span></span>  
  
|<span data-ttu-id="0e7cd-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-134">ColumnName</span></span>|<span data-ttu-id="0e7cd-135">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-136">TABLE_CATALOG</span></span>|<span data-ttu-id="0e7cd-137">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-137">String</span></span>|  
|<span data-ttu-id="0e7cd-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-139">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-139">String</span></span>|  
|<span data-ttu-id="0e7cd-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-140">TABLE_NAME</span></span>|<span data-ttu-id="0e7cd-141">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-141">String</span></span>|  
|<span data-ttu-id="0e7cd-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-142">COLUMN_NAME</span></span>|<span data-ttu-id="0e7cd-143">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-143">String</span></span>|  
|<span data-ttu-id="0e7cd-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-144">COLUMN_GUID</span></span>|<span data-ttu-id="0e7cd-145">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-145">Guid</span></span>|  
|<span data-ttu-id="0e7cd-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-146">COLUMN_PROPID</span></span>|<span data-ttu-id="0e7cd-147">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-147">Int64</span></span>|  
|<span data-ttu-id="0e7cd-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e7cd-149">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-149">Int64</span></span>|  
|<span data-ttu-id="0e7cd-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0e7cd-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0e7cd-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-151">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0e7cd-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0e7cd-153">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-153">String</span></span>|  
|<span data-ttu-id="0e7cd-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0e7cd-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="0e7cd-155">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-155">Int64</span></span>|  
|<span data-ttu-id="0e7cd-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-156">IS_NULLABLE</span></span>|<span data-ttu-id="0e7cd-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-157">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-158">DATA_TYPE</span></span>|<span data-ttu-id="0e7cd-159">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-159">Int32</span></span>|  
|<span data-ttu-id="0e7cd-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-160">TYPE_GUID</span></span>|<span data-ttu-id="0e7cd-161">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-161">Guid</span></span>|  
|<span data-ttu-id="0e7cd-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e7cd-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0e7cd-163">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-163">Int64</span></span>|  
|<span data-ttu-id="0e7cd-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e7cd-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0e7cd-165">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-165">Int64</span></span>|  
|<span data-ttu-id="0e7cd-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0e7cd-167">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-167">Int32</span></span>|  
|<span data-ttu-id="0e7cd-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="0e7cd-169">Int16</span><span class="sxs-lookup"><span data-stu-id="0e7cd-169">Int16</span></span>|  
|<span data-ttu-id="0e7cd-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="0e7cd-171">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-171">Int64</span></span>|  
|<span data-ttu-id="0e7cd-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0e7cd-173">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-173">String</span></span>|  
|<span data-ttu-id="0e7cd-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0e7cd-175">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-175">String</span></span>|  
|<span data-ttu-id="0e7cd-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0e7cd-177">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-177">String</span></span>|  
|<span data-ttu-id="0e7cd-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="0e7cd-179">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-179">String</span></span>|  
|<span data-ttu-id="0e7cd-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0e7cd-181">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-181">String</span></span>|  
|<span data-ttu-id="0e7cd-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-182">COLLATION_NAME</span></span>|<span data-ttu-id="0e7cd-183">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-183">String</span></span>|  
|<span data-ttu-id="0e7cd-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0e7cd-185">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-185">String</span></span>|  
|<span data-ttu-id="0e7cd-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0e7cd-187">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-187">String</span></span>|  
|<span data-ttu-id="0e7cd-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-188">DOMAIN_NAME</span></span>|<span data-ttu-id="0e7cd-189">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-189">String</span></span>|  
|<span data-ttu-id="0e7cd-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-190">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-191">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-191">String</span></span>|  
|<span data-ttu-id="0e7cd-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-192">COLUMN_LCID</span></span>|<span data-ttu-id="0e7cd-193">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-193">Int32</span></span>|  
|<span data-ttu-id="0e7cd-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="0e7cd-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="0e7cd-195">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-195">Int32</span></span>|  
|<span data-ttu-id="0e7cd-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-196">COLUMN_SORTID</span></span>|<span data-ttu-id="0e7cd-197">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-197">Int32</span></span>|  
|<span data-ttu-id="0e7cd-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="0e7cd-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="0e7cd-199">Byte[]</span></span>|  
|<span data-ttu-id="0e7cd-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-200">IS_COMPUTED</span></span>|<span data-ttu-id="0e7cd-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0e7cd-202">手順</span><span class="sxs-lookup"><span data-stu-id="0e7cd-202">Procedures</span></span>  
  
|<span data-ttu-id="0e7cd-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-203">ColumnName</span></span>|<span data-ttu-id="0e7cd-204">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0e7cd-206">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-206">String</span></span>|  
|<span data-ttu-id="0e7cd-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-208">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-208">String</span></span>|  
|<span data-ttu-id="0e7cd-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="0e7cd-210">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-210">String</span></span>|  
|<span data-ttu-id="0e7cd-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0e7cd-212">Int16</span><span class="sxs-lookup"><span data-stu-id="0e7cd-212">Int16</span></span>|  
|<span data-ttu-id="0e7cd-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0e7cd-214">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-214">String</span></span>|  
|<span data-ttu-id="0e7cd-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-215">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-216">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-216">String</span></span>|  
|<span data-ttu-id="0e7cd-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-217">DATE_CREATED</span></span>|<span data-ttu-id="0e7cd-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-218">DateTime</span></span>|  
|<span data-ttu-id="0e7cd-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-219">DATE_MODIFIED</span></span>|<span data-ttu-id="0e7cd-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="0e7cd-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0e7cd-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="0e7cd-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-222">ColumnName</span></span>|<span data-ttu-id="0e7cd-223">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0e7cd-225">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-225">String</span></span>|  
|<span data-ttu-id="0e7cd-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-227">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-227">String</span></span>|  
|<span data-ttu-id="0e7cd-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="0e7cd-229">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-229">String</span></span>|  
|<span data-ttu-id="0e7cd-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-230">PARAMETER_NAME</span></span>|<span data-ttu-id="0e7cd-231">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-231">String</span></span>|  
|<span data-ttu-id="0e7cd-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e7cd-233">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-233">Int32</span></span>|  
|<span data-ttu-id="0e7cd-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="0e7cd-235">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-235">Int32</span></span>|  
|<span data-ttu-id="0e7cd-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0e7cd-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="0e7cd-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-237">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0e7cd-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="0e7cd-239">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-239">String</span></span>|  
|<span data-ttu-id="0e7cd-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-240">IS_NULLABLE</span></span>|<span data-ttu-id="0e7cd-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-241">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-242">DATA_TYPE</span></span>|<span data-ttu-id="0e7cd-243">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-243">Int32</span></span>|  
|<span data-ttu-id="0e7cd-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e7cd-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0e7cd-245">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-245">Int64</span></span>|  
|<span data-ttu-id="0e7cd-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e7cd-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0e7cd-247">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-247">Int64</span></span>|  
|<span data-ttu-id="0e7cd-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0e7cd-249">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-249">Int32</span></span>|  
|<span data-ttu-id="0e7cd-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="0e7cd-251">Int16</span><span class="sxs-lookup"><span data-stu-id="0e7cd-251">Int16</span></span>|  
|<span data-ttu-id="0e7cd-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-252">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-253">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-253">String</span></span>|  
|<span data-ttu-id="0e7cd-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-254">TYPE_NAME</span></span>|<span data-ttu-id="0e7cd-255">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-255">String</span></span>|  
|<span data-ttu-id="0e7cd-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="0e7cd-257">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="0e7cd-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="0e7cd-258">Catalog</span></span>  
  
|<span data-ttu-id="0e7cd-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-259">ColumnName</span></span>|<span data-ttu-id="0e7cd-260">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-261">CATALOG_NAME</span></span>|<span data-ttu-id="0e7cd-262">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-262">String</span></span>|  
|<span data-ttu-id="0e7cd-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-263">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-264">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0e7cd-265">Indexes</span><span class="sxs-lookup"><span data-stu-id="0e7cd-265">Indexes</span></span>  
  
|<span data-ttu-id="0e7cd-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-266">ColumnName</span></span>|<span data-ttu-id="0e7cd-267">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-268">TABLE_CATALOG</span></span>|<span data-ttu-id="0e7cd-269">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-269">String</span></span>|  
|<span data-ttu-id="0e7cd-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-271">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-271">String</span></span>|  
|<span data-ttu-id="0e7cd-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-272">TABLE_NAME</span></span>|<span data-ttu-id="0e7cd-273">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-273">String</span></span>|  
|<span data-ttu-id="0e7cd-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-274">INDEX_CATALOG</span></span>|<span data-ttu-id="0e7cd-275">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-275">String</span></span>|  
|<span data-ttu-id="0e7cd-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="0e7cd-277">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-277">String</span></span>|  
|<span data-ttu-id="0e7cd-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-278">INDEX_NAME</span></span>|<span data-ttu-id="0e7cd-279">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-279">String</span></span>|  
|<span data-ttu-id="0e7cd-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0e7cd-280">PRIMARY_KEY</span></span>|<span data-ttu-id="0e7cd-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-281">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-282">UNIQUE</span></span>|<span data-ttu-id="0e7cd-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-283">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-284">CLUSTERED</span></span>|<span data-ttu-id="0e7cd-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-285">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-286">TYPE</span></span>|<span data-ttu-id="0e7cd-287">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-287">Int32</span></span>|  
|<span data-ttu-id="0e7cd-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0e7cd-288">FILL_FACTOR</span></span>|<span data-ttu-id="0e7cd-289">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-289">Int32</span></span>|  
|<span data-ttu-id="0e7cd-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-290">INITIAL_SIZE</span></span>|<span data-ttu-id="0e7cd-291">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-291">Int32</span></span>|  
|<span data-ttu-id="0e7cd-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="0e7cd-292">NULLS</span></span>|<span data-ttu-id="0e7cd-293">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-293">Int32</span></span>|  
|<span data-ttu-id="0e7cd-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0e7cd-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0e7cd-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-295">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-296">AUTO_UPDATE</span></span>|<span data-ttu-id="0e7cd-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-297">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-298">NULL_COLLATION</span></span>|<span data-ttu-id="0e7cd-299">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-299">Int32</span></span>|  
|<span data-ttu-id="0e7cd-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e7cd-301">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-301">Int64</span></span>|  
|<span data-ttu-id="0e7cd-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-302">COLUMN_NAME</span></span>|<span data-ttu-id="0e7cd-303">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-303">String</span></span>|  
|<span data-ttu-id="0e7cd-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-304">COLUMN_GUID</span></span>|<span data-ttu-id="0e7cd-305">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-305">Guid</span></span>|  
|<span data-ttu-id="0e7cd-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-306">COLUMN_PROPID</span></span>|<span data-ttu-id="0e7cd-307">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-307">Int64</span></span>|  
|<span data-ttu-id="0e7cd-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-308">COLLATION</span></span>|<span data-ttu-id="0e7cd-309">Int16</span><span class="sxs-lookup"><span data-stu-id="0e7cd-309">Int16</span></span>|  
|<span data-ttu-id="0e7cd-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="0e7cd-310">CARDINALITY</span></span>|<span data-ttu-id="0e7cd-311">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="0e7cd-311">Decimal</span></span>|  
|<span data-ttu-id="0e7cd-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="0e7cd-312">PAGES</span></span>|<span data-ttu-id="0e7cd-313">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-313">Int32</span></span>|  
|<span data-ttu-id="0e7cd-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-314">FILTER_CONDITION</span></span>|<span data-ttu-id="0e7cd-315">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-315">String</span></span>|  
|<span data-ttu-id="0e7cd-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-316">INTEGRATED</span></span>|<span data-ttu-id="0e7cd-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="0e7cd-318">Microsoft Oracle OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="0e7cd-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="0e7cd-319">Microsoft Oracle OLE DB Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0e7cd-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0e7cd-320">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="0e7cd-320">Tables</span></span>  
  
-   <span data-ttu-id="0e7cd-321">列</span><span class="sxs-lookup"><span data-stu-id="0e7cd-321">Columns</span></span>  
  
-   <span data-ttu-id="0e7cd-322">手順</span><span class="sxs-lookup"><span data-stu-id="0e7cd-322">Procedures</span></span>  
  
-   <span data-ttu-id="0e7cd-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0e7cd-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="0e7cd-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0e7cd-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0e7cd-325">ビュー</span><span class="sxs-lookup"><span data-stu-id="0e7cd-325">Views</span></span>  
  
-   <span data-ttu-id="0e7cd-326">Indexes</span><span class="sxs-lookup"><span data-stu-id="0e7cd-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0e7cd-327">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="0e7cd-327">Tables</span></span>  
  
|<span data-ttu-id="0e7cd-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-328">ColumnName</span></span>|<span data-ttu-id="0e7cd-329">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-330">TABLE_CATALOG</span></span>|<span data-ttu-id="0e7cd-331">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-331">String</span></span>|  
|<span data-ttu-id="0e7cd-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-333">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-333">String</span></span>|  
|<span data-ttu-id="0e7cd-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-334">TABLE_NAME</span></span>|<span data-ttu-id="0e7cd-335">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-335">String</span></span>|  
|<span data-ttu-id="0e7cd-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-336">TABLE_TYPE</span></span>|<span data-ttu-id="0e7cd-337">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-337">String</span></span>|  
|<span data-ttu-id="0e7cd-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-338">TABLE_GUID</span></span>|<span data-ttu-id="0e7cd-339">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-339">Guid</span></span>|  
|<span data-ttu-id="0e7cd-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-340">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-341">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-341">String</span></span>|  
|<span data-ttu-id="0e7cd-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-342">TABLE_PROPID</span></span>|<span data-ttu-id="0e7cd-343">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-343">Int64</span></span>|  
|<span data-ttu-id="0e7cd-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-344">DATE_CREATED</span></span>|<span data-ttu-id="0e7cd-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-345">DateTime</span></span>|  
|<span data-ttu-id="0e7cd-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-346">DATE_MODIFIED</span></span>|<span data-ttu-id="0e7cd-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0e7cd-348">列</span><span class="sxs-lookup"><span data-stu-id="0e7cd-348">Columns</span></span>  
  
|<span data-ttu-id="0e7cd-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-349">ColumnName</span></span>|<span data-ttu-id="0e7cd-350">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-351">TABLE_CATALOG</span></span>|<span data-ttu-id="0e7cd-352">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-352">String</span></span>|  
|<span data-ttu-id="0e7cd-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-354">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-354">String</span></span>|  
|<span data-ttu-id="0e7cd-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-355">TABLE_NAME</span></span>|<span data-ttu-id="0e7cd-356">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-356">String</span></span>|  
|<span data-ttu-id="0e7cd-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-357">COLUMN_NAME</span></span>|<span data-ttu-id="0e7cd-358">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-358">String</span></span>|  
|<span data-ttu-id="0e7cd-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-359">COLUMN_GUID</span></span>|<span data-ttu-id="0e7cd-360">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-360">Guid</span></span>|  
|<span data-ttu-id="0e7cd-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-361">COLUMN_PROPID</span></span>|<span data-ttu-id="0e7cd-362">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-362">Int64</span></span>|  
|<span data-ttu-id="0e7cd-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e7cd-364">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-364">Int64</span></span>|  
|<span data-ttu-id="0e7cd-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0e7cd-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0e7cd-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-366">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0e7cd-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0e7cd-368">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-368">String</span></span>|  
|<span data-ttu-id="0e7cd-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0e7cd-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="0e7cd-370">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-370">Int64</span></span>|  
|<span data-ttu-id="0e7cd-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-371">IS_NULLABLE</span></span>|<span data-ttu-id="0e7cd-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-372">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-373">DATA_TYPE</span></span>|<span data-ttu-id="0e7cd-374">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-374">Int32</span></span>|  
|<span data-ttu-id="0e7cd-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-375">TYPE_GUID</span></span>|<span data-ttu-id="0e7cd-376">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-376">Guid</span></span>|  
|<span data-ttu-id="0e7cd-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e7cd-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0e7cd-378">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-378">Int64</span></span>|  
|<span data-ttu-id="0e7cd-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e7cd-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0e7cd-380">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-380">Int64</span></span>|  
|<span data-ttu-id="0e7cd-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0e7cd-382">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-382">Int32</span></span>|  
|<span data-ttu-id="0e7cd-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="0e7cd-384">Int16</span><span class="sxs-lookup"><span data-stu-id="0e7cd-384">Int16</span></span>|  
|<span data-ttu-id="0e7cd-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="0e7cd-386">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-386">Int64</span></span>|  
|<span data-ttu-id="0e7cd-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0e7cd-388">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-388">String</span></span>|  
|<span data-ttu-id="0e7cd-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0e7cd-390">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-390">String</span></span>|  
|<span data-ttu-id="0e7cd-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0e7cd-392">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-392">String</span></span>|  
|<span data-ttu-id="0e7cd-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="0e7cd-394">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-394">String</span></span>|  
|<span data-ttu-id="0e7cd-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0e7cd-396">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-396">String</span></span>|  
|<span data-ttu-id="0e7cd-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-397">COLLATION_NAME</span></span>|<span data-ttu-id="0e7cd-398">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-398">String</span></span>|  
|<span data-ttu-id="0e7cd-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0e7cd-400">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-400">String</span></span>|  
|<span data-ttu-id="0e7cd-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0e7cd-402">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-402">String</span></span>|  
|<span data-ttu-id="0e7cd-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-403">DOMAIN_NAME</span></span>|<span data-ttu-id="0e7cd-404">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-404">String</span></span>|  
|<span data-ttu-id="0e7cd-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-405">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-406">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0e7cd-407">手順</span><span class="sxs-lookup"><span data-stu-id="0e7cd-407">Procedures</span></span>  
  
|<span data-ttu-id="0e7cd-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-408">ColumnName</span></span>|<span data-ttu-id="0e7cd-409">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0e7cd-411">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-411">String</span></span>|  
|<span data-ttu-id="0e7cd-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-413">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-413">String</span></span>|  
|<span data-ttu-id="0e7cd-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="0e7cd-415">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-415">String</span></span>|  
|<span data-ttu-id="0e7cd-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0e7cd-417">Int16</span><span class="sxs-lookup"><span data-stu-id="0e7cd-417">Int16</span></span>|  
|<span data-ttu-id="0e7cd-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0e7cd-419">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-419">String</span></span>|  
|<span data-ttu-id="0e7cd-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-420">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-421">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-421">String</span></span>|  
|<span data-ttu-id="0e7cd-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-422">DATE_CREATED</span></span>|<span data-ttu-id="0e7cd-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-423">DateTime</span></span>|  
|<span data-ttu-id="0e7cd-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-424">DATE_MODIFIED</span></span>|<span data-ttu-id="0e7cd-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="0e7cd-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0e7cd-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="0e7cd-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-427">ColumnName</span></span>|<span data-ttu-id="0e7cd-428">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0e7cd-430">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-430">String</span></span>|  
|<span data-ttu-id="0e7cd-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-432">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-432">String</span></span>|  
|<span data-ttu-id="0e7cd-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="0e7cd-434">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-434">String</span></span>|  
|<span data-ttu-id="0e7cd-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-435">COLUMN_NAME</span></span>|<span data-ttu-id="0e7cd-436">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-436">String</span></span>|  
|<span data-ttu-id="0e7cd-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-437">COLUMN_GUID</span></span>|<span data-ttu-id="0e7cd-438">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-438">Guid</span></span>|  
|<span data-ttu-id="0e7cd-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-439">COLUMN_PROPID</span></span>|<span data-ttu-id="0e7cd-440">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-440">Int64</span></span>|  
|<span data-ttu-id="0e7cd-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="0e7cd-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="0e7cd-442">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-442">Int64</span></span>|  
|<span data-ttu-id="0e7cd-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e7cd-444">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-444">Int64</span></span>|  
|<span data-ttu-id="0e7cd-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-445">IS_NULLABLE</span></span>|<span data-ttu-id="0e7cd-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-446">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-447">DATA_TYPE</span></span>|<span data-ttu-id="0e7cd-448">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-448">Int32</span></span>|  
|<span data-ttu-id="0e7cd-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-449">TYPE_GUID</span></span>|<span data-ttu-id="0e7cd-450">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-450">Guid</span></span>|  
|<span data-ttu-id="0e7cd-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e7cd-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0e7cd-452">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-452">Int64</span></span>|  
|<span data-ttu-id="0e7cd-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e7cd-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0e7cd-454">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-454">Int64</span></span>|  
|<span data-ttu-id="0e7cd-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0e7cd-456">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-456">Int32</span></span>|  
|<span data-ttu-id="0e7cd-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="0e7cd-458">Int16</span><span class="sxs-lookup"><span data-stu-id="0e7cd-458">Int16</span></span>|  
|<span data-ttu-id="0e7cd-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-459">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-460">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-460">String</span></span>|  
|<span data-ttu-id="0e7cd-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="0e7cd-461">OVERLOAD</span></span>|<span data-ttu-id="0e7cd-462">Int16</span><span class="sxs-lookup"><span data-stu-id="0e7cd-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="0e7cd-463">ビュー</span><span class="sxs-lookup"><span data-stu-id="0e7cd-463">Views</span></span>  
  
|<span data-ttu-id="0e7cd-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-464">ColumnName</span></span>|<span data-ttu-id="0e7cd-465">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-466">TABLE_CATALOG</span></span>|<span data-ttu-id="0e7cd-467">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-467">String</span></span>|  
|<span data-ttu-id="0e7cd-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-469">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-469">String</span></span>|  
|<span data-ttu-id="0e7cd-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-470">TABLE_NAME</span></span>|<span data-ttu-id="0e7cd-471">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-471">String</span></span>|  
|<span data-ttu-id="0e7cd-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="0e7cd-473">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-473">String</span></span>|  
|<span data-ttu-id="0e7cd-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-474">CHECK_OPTION</span></span>|<span data-ttu-id="0e7cd-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-475">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-476">IS_UPDATABLE</span></span>|<span data-ttu-id="0e7cd-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-477">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-478">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-479">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-479">String</span></span>|  
|<span data-ttu-id="0e7cd-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-480">DATE_CREATED</span></span>|<span data-ttu-id="0e7cd-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-481">DateTime</span></span>|  
|<span data-ttu-id="0e7cd-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-482">DATE_MODIFIED</span></span>|<span data-ttu-id="0e7cd-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0e7cd-484">Indexes</span><span class="sxs-lookup"><span data-stu-id="0e7cd-484">Indexes</span></span>  
  
|<span data-ttu-id="0e7cd-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-485">ColumnName</span></span>|<span data-ttu-id="0e7cd-486">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-487">TABLE_CATALOG</span></span>|<span data-ttu-id="0e7cd-488">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-488">String</span></span>|  
|<span data-ttu-id="0e7cd-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-490">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-490">String</span></span>|  
|<span data-ttu-id="0e7cd-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-491">TABLE_NAME</span></span>|<span data-ttu-id="0e7cd-492">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-492">String</span></span>|  
|<span data-ttu-id="0e7cd-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-493">INDEX_CATALOG</span></span>|<span data-ttu-id="0e7cd-494">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-494">String</span></span>|  
|<span data-ttu-id="0e7cd-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="0e7cd-496">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-496">String</span></span>|  
|<span data-ttu-id="0e7cd-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-497">INDEX_NAME</span></span>|<span data-ttu-id="0e7cd-498">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-498">String</span></span>|  
|<span data-ttu-id="0e7cd-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0e7cd-499">PRIMARY_KEY</span></span>|<span data-ttu-id="0e7cd-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-500">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-501">UNIQUE</span></span>|<span data-ttu-id="0e7cd-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-502">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-503">CLUSTERED</span></span>|<span data-ttu-id="0e7cd-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-504">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-505">TYPE</span></span>|<span data-ttu-id="0e7cd-506">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-506">Int32</span></span>|  
|<span data-ttu-id="0e7cd-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0e7cd-507">FILL_FACTOR</span></span>|<span data-ttu-id="0e7cd-508">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-508">Int32</span></span>|  
|<span data-ttu-id="0e7cd-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-509">INITIAL_SIZE</span></span>|<span data-ttu-id="0e7cd-510">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-510">Int32</span></span>|  
|<span data-ttu-id="0e7cd-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="0e7cd-511">NULLS</span></span>|<span data-ttu-id="0e7cd-512">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-512">Int32</span></span>|  
|<span data-ttu-id="0e7cd-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0e7cd-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0e7cd-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-514">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-515">AUTO_UPDATE</span></span>|<span data-ttu-id="0e7cd-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-516">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-517">NULL_COLLATION</span></span>|<span data-ttu-id="0e7cd-518">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-518">Int32</span></span>|  
|<span data-ttu-id="0e7cd-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e7cd-520">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-520">Int64</span></span>|  
|<span data-ttu-id="0e7cd-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-521">COLUMN_NAME</span></span>|<span data-ttu-id="0e7cd-522">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-522">String</span></span>|  
|<span data-ttu-id="0e7cd-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-523">COLUMN_GUID</span></span>|<span data-ttu-id="0e7cd-524">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-524">Guid</span></span>|  
|<span data-ttu-id="0e7cd-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-525">COLUMN_PROPID</span></span>|<span data-ttu-id="0e7cd-526">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-526">Int64</span></span>|  
|<span data-ttu-id="0e7cd-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-527">COLLATION</span></span>|<span data-ttu-id="0e7cd-528">Int16</span><span class="sxs-lookup"><span data-stu-id="0e7cd-528">Int16</span></span>|  
|<span data-ttu-id="0e7cd-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="0e7cd-529">CARDINALITY</span></span>|<span data-ttu-id="0e7cd-530">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="0e7cd-530">Decimal</span></span>|  
|<span data-ttu-id="0e7cd-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="0e7cd-531">PAGES</span></span>|<span data-ttu-id="0e7cd-532">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-532">Int32</span></span>|  
|<span data-ttu-id="0e7cd-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-533">FILTER_CONDITION</span></span>|<span data-ttu-id="0e7cd-534">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-534">String</span></span>|  
|<span data-ttu-id="0e7cd-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-535">INTEGRATED</span></span>|<span data-ttu-id="0e7cd-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="0e7cd-537">Microsoft Jet OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="0e7cd-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="0e7cd-538">Microsoft Jet OLE DB Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0e7cd-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0e7cd-539">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="0e7cd-539">Tables</span></span>  
  
-   <span data-ttu-id="0e7cd-540">列</span><span class="sxs-lookup"><span data-stu-id="0e7cd-540">Columns</span></span>  
  
-   <span data-ttu-id="0e7cd-541">手順</span><span class="sxs-lookup"><span data-stu-id="0e7cd-541">Procedures</span></span>  
  
-   <span data-ttu-id="0e7cd-542">ビュー</span><span class="sxs-lookup"><span data-stu-id="0e7cd-542">Views</span></span>  
  
-   <span data-ttu-id="0e7cd-543">Indexes</span><span class="sxs-lookup"><span data-stu-id="0e7cd-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0e7cd-544">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="0e7cd-544">Tables</span></span>  
  
|<span data-ttu-id="0e7cd-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-545">ColumnName</span></span>|<span data-ttu-id="0e7cd-546">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-547">TABLE_CATALOG</span></span>|<span data-ttu-id="0e7cd-548">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-548">String</span></span>|  
|<span data-ttu-id="0e7cd-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-550">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-550">String</span></span>|  
|<span data-ttu-id="0e7cd-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-551">TABLE_NAME</span></span>|<span data-ttu-id="0e7cd-552">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-552">String</span></span>|  
|<span data-ttu-id="0e7cd-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-553">TABLE_TYPE</span></span>|<span data-ttu-id="0e7cd-554">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-554">String</span></span>|  
|<span data-ttu-id="0e7cd-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-555">TABLE_GUID</span></span>|<span data-ttu-id="0e7cd-556">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-556">Guid</span></span>|  
|<span data-ttu-id="0e7cd-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-557">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-558">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-558">String</span></span>|  
|<span data-ttu-id="0e7cd-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-559">TABLE_PROPID</span></span>|<span data-ttu-id="0e7cd-560">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-560">Int64</span></span>|  
|<span data-ttu-id="0e7cd-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-561">DATE_CREATED</span></span>|<span data-ttu-id="0e7cd-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-562">DateTime</span></span>|  
|<span data-ttu-id="0e7cd-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-563">DATE_MODIFIED</span></span>|<span data-ttu-id="0e7cd-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0e7cd-565">列</span><span class="sxs-lookup"><span data-stu-id="0e7cd-565">Columns</span></span>  
  
|<span data-ttu-id="0e7cd-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-566">ColumnName</span></span>|<span data-ttu-id="0e7cd-567">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-568">TABLE_CATALOG</span></span>|<span data-ttu-id="0e7cd-569">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-569">String</span></span>|  
|<span data-ttu-id="0e7cd-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-571">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-571">String</span></span>|  
|<span data-ttu-id="0e7cd-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-572">TABLE_NAME</span></span>|<span data-ttu-id="0e7cd-573">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-573">String</span></span>|  
|<span data-ttu-id="0e7cd-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-574">COLUMN_NAME</span></span>|<span data-ttu-id="0e7cd-575">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-575">String</span></span>|  
|<span data-ttu-id="0e7cd-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-576">COLUMN_GUID</span></span>|<span data-ttu-id="0e7cd-577">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-577">Guid</span></span>|  
|<span data-ttu-id="0e7cd-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-578">COLUMN_PROPID</span></span>|<span data-ttu-id="0e7cd-579">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-579">Int64</span></span>|  
|<span data-ttu-id="0e7cd-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e7cd-581">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-581">Int64</span></span>|  
|<span data-ttu-id="0e7cd-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0e7cd-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0e7cd-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-583">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0e7cd-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0e7cd-585">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-585">String</span></span>|  
|<span data-ttu-id="0e7cd-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0e7cd-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="0e7cd-587">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-587">Int64</span></span>|  
|<span data-ttu-id="0e7cd-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-588">IS_NULLABLE</span></span>|<span data-ttu-id="0e7cd-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-589">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-590">DATA_TYPE</span></span>|<span data-ttu-id="0e7cd-591">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-591">Int32</span></span>|  
|<span data-ttu-id="0e7cd-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-592">TYPE_GUID</span></span>|<span data-ttu-id="0e7cd-593">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-593">Guid</span></span>|  
|<span data-ttu-id="0e7cd-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e7cd-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0e7cd-595">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-595">Int64</span></span>|  
|<span data-ttu-id="0e7cd-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e7cd-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0e7cd-597">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-597">Int64</span></span>|  
|<span data-ttu-id="0e7cd-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0e7cd-599">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-599">Int32</span></span>|  
|<span data-ttu-id="0e7cd-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="0e7cd-601">Int16</span><span class="sxs-lookup"><span data-stu-id="0e7cd-601">Int16</span></span>|  
|<span data-ttu-id="0e7cd-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="0e7cd-603">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-603">Int64</span></span>|  
|<span data-ttu-id="0e7cd-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0e7cd-605">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-605">String</span></span>|  
|<span data-ttu-id="0e7cd-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0e7cd-607">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-607">String</span></span>|  
|<span data-ttu-id="0e7cd-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0e7cd-609">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-609">String</span></span>|  
|<span data-ttu-id="0e7cd-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="0e7cd-611">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-611">String</span></span>|  
|<span data-ttu-id="0e7cd-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0e7cd-613">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-613">String</span></span>|  
|<span data-ttu-id="0e7cd-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-614">COLLATION_NAME</span></span>|<span data-ttu-id="0e7cd-615">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-615">String</span></span>|  
|<span data-ttu-id="0e7cd-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0e7cd-617">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-617">String</span></span>|  
|<span data-ttu-id="0e7cd-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0e7cd-619">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-619">String</span></span>|  
|<span data-ttu-id="0e7cd-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-620">DOMAIN_NAME</span></span>|<span data-ttu-id="0e7cd-621">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-621">String</span></span>|  
|<span data-ttu-id="0e7cd-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-622">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-623">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0e7cd-624">手順</span><span class="sxs-lookup"><span data-stu-id="0e7cd-624">Procedures</span></span>  
  
|<span data-ttu-id="0e7cd-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-625">ColumnName</span></span>|<span data-ttu-id="0e7cd-626">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0e7cd-628">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-628">String</span></span>|  
|<span data-ttu-id="0e7cd-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-630">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-630">String</span></span>|  
|<span data-ttu-id="0e7cd-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="0e7cd-632">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-632">String</span></span>|  
|<span data-ttu-id="0e7cd-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0e7cd-634">Int16</span><span class="sxs-lookup"><span data-stu-id="0e7cd-634">Int16</span></span>|  
|<span data-ttu-id="0e7cd-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0e7cd-636">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-636">String</span></span>|  
|<span data-ttu-id="0e7cd-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-637">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-638">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-638">String</span></span>|  
|<span data-ttu-id="0e7cd-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-639">DATE_CREATED</span></span>|<span data-ttu-id="0e7cd-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-640">DateTime</span></span>|  
|<span data-ttu-id="0e7cd-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-641">DATE_MODIFIED</span></span>|<span data-ttu-id="0e7cd-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="0e7cd-643">ビュー</span><span class="sxs-lookup"><span data-stu-id="0e7cd-643">Views</span></span>  
  
|<span data-ttu-id="0e7cd-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-644">ColumnName</span></span>|<span data-ttu-id="0e7cd-645">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-646">TABLE_CATALOG</span></span>|<span data-ttu-id="0e7cd-647">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-647">String</span></span>|  
|<span data-ttu-id="0e7cd-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-649">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-649">String</span></span>|  
|<span data-ttu-id="0e7cd-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-650">TABLE_NAME</span></span>|<span data-ttu-id="0e7cd-651">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-651">String</span></span>|  
|<span data-ttu-id="0e7cd-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="0e7cd-653">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-653">String</span></span>|  
|<span data-ttu-id="0e7cd-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-654">CHECK_OPTION</span></span>|<span data-ttu-id="0e7cd-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-655">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-656">IS_UPDATABLE</span></span>|<span data-ttu-id="0e7cd-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-657">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-658">DESCRIPTION</span></span>|<span data-ttu-id="0e7cd-659">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-659">String</span></span>|  
|<span data-ttu-id="0e7cd-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-660">DATE_CREATED</span></span>|<span data-ttu-id="0e7cd-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-661">DateTime</span></span>|  
|<span data-ttu-id="0e7cd-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-662">DATE_MODIFIED</span></span>|<span data-ttu-id="0e7cd-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e7cd-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0e7cd-664">Indexes</span><span class="sxs-lookup"><span data-stu-id="0e7cd-664">Indexes</span></span>  
  
|<span data-ttu-id="0e7cd-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e7cd-665">ColumnName</span></span>|<span data-ttu-id="0e7cd-666">DataType</span><span class="sxs-lookup"><span data-stu-id="0e7cd-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0e7cd-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-667">TABLE_CATALOG</span></span>|<span data-ttu-id="0e7cd-668">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-668">String</span></span>|  
|<span data-ttu-id="0e7cd-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="0e7cd-670">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-670">String</span></span>|  
|<span data-ttu-id="0e7cd-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-671">TABLE_NAME</span></span>|<span data-ttu-id="0e7cd-672">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-672">String</span></span>|  
|<span data-ttu-id="0e7cd-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e7cd-673">INDEX_CATALOG</span></span>|<span data-ttu-id="0e7cd-674">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-674">String</span></span>|  
|<span data-ttu-id="0e7cd-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e7cd-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="0e7cd-676">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-676">String</span></span>|  
|<span data-ttu-id="0e7cd-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-677">INDEX_NAME</span></span>|<span data-ttu-id="0e7cd-678">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-678">String</span></span>|  
|<span data-ttu-id="0e7cd-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0e7cd-679">PRIMARY_KEY</span></span>|<span data-ttu-id="0e7cd-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-680">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-681">UNIQUE</span></span>|<span data-ttu-id="0e7cd-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-682">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-683">CLUSTERED</span></span>|<span data-ttu-id="0e7cd-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-684">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-685">TYPE</span></span>|<span data-ttu-id="0e7cd-686">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-686">Int32</span></span>|  
|<span data-ttu-id="0e7cd-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0e7cd-687">FILL_FACTOR</span></span>|<span data-ttu-id="0e7cd-688">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-688">Int32</span></span>|  
|<span data-ttu-id="0e7cd-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-689">INITIAL_SIZE</span></span>|<span data-ttu-id="0e7cd-690">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-690">Int32</span></span>|  
|<span data-ttu-id="0e7cd-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="0e7cd-691">NULLS</span></span>|<span data-ttu-id="0e7cd-692">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-692">Int32</span></span>|  
|<span data-ttu-id="0e7cd-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0e7cd-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0e7cd-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-694">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0e7cd-695">AUTO_UPDATE</span></span>|<span data-ttu-id="0e7cd-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e7cd-696">Boolean</span></span>|  
|<span data-ttu-id="0e7cd-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-697">NULL_COLLATION</span></span>|<span data-ttu-id="0e7cd-698">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-698">Int32</span></span>|  
|<span data-ttu-id="0e7cd-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e7cd-700">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-700">Int64</span></span>|  
|<span data-ttu-id="0e7cd-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e7cd-701">COLUMN_NAME</span></span>|<span data-ttu-id="0e7cd-702">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-702">String</span></span>|  
|<span data-ttu-id="0e7cd-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-703">COLUMN_GUID</span></span>|<span data-ttu-id="0e7cd-704">Guid</span><span class="sxs-lookup"><span data-stu-id="0e7cd-704">Guid</span></span>|  
|<span data-ttu-id="0e7cd-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0e7cd-705">COLUMN_PROPID</span></span>|<span data-ttu-id="0e7cd-706">Int64</span><span class="sxs-lookup"><span data-stu-id="0e7cd-706">Int64</span></span>|  
|<span data-ttu-id="0e7cd-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-707">COLLATION</span></span>|<span data-ttu-id="0e7cd-708">Int16</span><span class="sxs-lookup"><span data-stu-id="0e7cd-708">Int16</span></span>|  
|<span data-ttu-id="0e7cd-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="0e7cd-709">CARDINALITY</span></span>|<span data-ttu-id="0e7cd-710">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="0e7cd-710">Decimal</span></span>|  
|<span data-ttu-id="0e7cd-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="0e7cd-711">PAGES</span></span>|<span data-ttu-id="0e7cd-712">Int32</span><span class="sxs-lookup"><span data-stu-id="0e7cd-712">Int32</span></span>|  
|<span data-ttu-id="0e7cd-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0e7cd-713">FILTER_CONDITION</span></span>|<span data-ttu-id="0e7cd-714">String</span><span class="sxs-lookup"><span data-stu-id="0e7cd-714">String</span></span>|  
|<span data-ttu-id="0e7cd-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="0e7cd-715">INTEGRATED</span></span>|<span data-ttu-id="0e7cd-716">ブール型</span><span class="sxs-lookup"><span data-stu-id="0e7cd-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e7cd-717">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e7cd-717">See Also</span></span>  
 [<span data-ttu-id="0e7cd-718">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="0e7cd-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
