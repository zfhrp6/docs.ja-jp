---
title: ODBC スキーマ コレクション
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: 36d0859b897bfcea33803c219ade14722ed90421
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="177f7-102">ODBC スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="177f7-102">ODBC Schema Collections</span></span>
<span data-ttu-id="177f7-103">ここでは、Microsoft SQL Server、Oracle、および Microsoft Jet 用の各 ODBC ドライバーでのスキーマ コレクションのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="177f7-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="177f7-104">Microsoft SQL Server ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="177f7-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="177f7-105">Microsoft SQL Server ODBC Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="177f7-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="177f7-106">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="177f7-106">Tables</span></span>  
  
-   <span data-ttu-id="177f7-107">Indexes</span><span class="sxs-lookup"><span data-stu-id="177f7-107">Indexes</span></span>  
  
-   <span data-ttu-id="177f7-108">列</span><span class="sxs-lookup"><span data-stu-id="177f7-108">Columns</span></span>  
  
-   <span data-ttu-id="177f7-109">手順</span><span class="sxs-lookup"><span data-stu-id="177f7-109">Procedures</span></span>  
  
-   <span data-ttu-id="177f7-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="177f7-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="177f7-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="177f7-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="177f7-112">ビュー</span><span class="sxs-lookup"><span data-stu-id="177f7-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="177f7-113">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="177f7-113">Tables and Views</span></span>  
  
|<span data-ttu-id="177f7-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-114">ColumnName</span></span>|<span data-ttu-id="177f7-115">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="177f7-116">TABLE_CAT</span></span>|<span data-ttu-id="177f7-117">String</span><span class="sxs-lookup"><span data-stu-id="177f7-117">String</span></span>|  
|<span data-ttu-id="177f7-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="177f7-118">TABLE_SCHEM</span></span>|<span data-ttu-id="177f7-119">String</span><span class="sxs-lookup"><span data-stu-id="177f7-119">String</span></span>|  
|<span data-ttu-id="177f7-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-120">TABLE_NAME</span></span>|<span data-ttu-id="177f7-121">String</span><span class="sxs-lookup"><span data-stu-id="177f7-121">String</span></span>|  
|<span data-ttu-id="177f7-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-122">TABLE_TYPE</span></span>|<span data-ttu-id="177f7-123">String</span><span class="sxs-lookup"><span data-stu-id="177f7-123">String</span></span>|  
|<span data-ttu-id="177f7-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-124">REMARKS</span></span>|<span data-ttu-id="177f7-125">String</span><span class="sxs-lookup"><span data-stu-id="177f7-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="177f7-126">Indexes</span><span class="sxs-lookup"><span data-stu-id="177f7-126">Indexes</span></span>  
  
|<span data-ttu-id="177f7-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-127">ColumnName</span></span>|<span data-ttu-id="177f7-128">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="177f7-129">TABLE_CAT</span></span>|<span data-ttu-id="177f7-130">String</span><span class="sxs-lookup"><span data-stu-id="177f7-130">String</span></span>|  
|<span data-ttu-id="177f7-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="177f7-131">TABLE_SCHEM</span></span>|<span data-ttu-id="177f7-132">String</span><span class="sxs-lookup"><span data-stu-id="177f7-132">String</span></span>|  
|<span data-ttu-id="177f7-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-133">TABLE_NAME</span></span>|<span data-ttu-id="177f7-134">String</span><span class="sxs-lookup"><span data-stu-id="177f7-134">String</span></span>|  
|<span data-ttu-id="177f7-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="177f7-135">NON_UNIQUE</span></span>|<span data-ttu-id="177f7-136">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-136">Int16</span></span>|  
|<span data-ttu-id="177f7-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="177f7-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="177f7-138">String</span><span class="sxs-lookup"><span data-stu-id="177f7-138">String</span></span>|  
|<span data-ttu-id="177f7-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-139">INDEX_NAME</span></span>|<span data-ttu-id="177f7-140">String</span><span class="sxs-lookup"><span data-stu-id="177f7-140">String</span></span>|  
|<span data-ttu-id="177f7-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-141">TYPE</span></span>|<span data-ttu-id="177f7-142">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-142">Int16</span></span>|  
|<span data-ttu-id="177f7-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="177f7-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="177f7-144">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-144">Int16</span></span>|  
|<span data-ttu-id="177f7-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-145">COLUMN_NAME</span></span>|<span data-ttu-id="177f7-146">String</span><span class="sxs-lookup"><span data-stu-id="177f7-146">String</span></span>|  
|<span data-ttu-id="177f7-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="177f7-147">ASC_OR_DESC</span></span>|<span data-ttu-id="177f7-148">String</span><span class="sxs-lookup"><span data-stu-id="177f7-148">String</span></span>|  
|<span data-ttu-id="177f7-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="177f7-149">CARDINATLITY</span></span>|<span data-ttu-id="177f7-150">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-150">Int32</span></span>|  
|<span data-ttu-id="177f7-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="177f7-151">PAGES</span></span>|<span data-ttu-id="177f7-152">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-152">Int32</span></span>|  
|<span data-ttu-id="177f7-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="177f7-153">FILTER_CONDITION</span></span>|<span data-ttu-id="177f7-154">String</span><span class="sxs-lookup"><span data-stu-id="177f7-154">String</span></span>|  
|<span data-ttu-id="177f7-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="177f7-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="177f7-156">String</span><span class="sxs-lookup"><span data-stu-id="177f7-156">String</span></span>|  
|<span data-ttu-id="177f7-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="177f7-158">Byte</span><span class="sxs-lookup"><span data-stu-id="177f7-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="177f7-159">列</span><span class="sxs-lookup"><span data-stu-id="177f7-159">Columns</span></span>  
  
|<span data-ttu-id="177f7-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-160">ColumnName</span></span>|<span data-ttu-id="177f7-161">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="177f7-162">TABLE_CAT</span></span>|<span data-ttu-id="177f7-163">String</span><span class="sxs-lookup"><span data-stu-id="177f7-163">String</span></span>|  
|<span data-ttu-id="177f7-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="177f7-164">TABLE_SCHEM</span></span>|<span data-ttu-id="177f7-165">String</span><span class="sxs-lookup"><span data-stu-id="177f7-165">String</span></span>|  
|<span data-ttu-id="177f7-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-166">TABLE_NAME</span></span>|<span data-ttu-id="177f7-167">String</span><span class="sxs-lookup"><span data-stu-id="177f7-167">String</span></span>|  
|<span data-ttu-id="177f7-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-168">COLUMN_NAME</span></span>|<span data-ttu-id="177f7-169">String</span><span class="sxs-lookup"><span data-stu-id="177f7-169">String</span></span>|  
|<span data-ttu-id="177f7-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-170">DATA_TYPE</span></span>|<span data-ttu-id="177f7-171">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-171">Int16</span></span>|  
|<span data-ttu-id="177f7-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-172">TYPE_NAME</span></span>|<span data-ttu-id="177f7-173">String</span><span class="sxs-lookup"><span data-stu-id="177f7-173">String</span></span>|  
|<span data-ttu-id="177f7-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="177f7-174">COLUMN_SIZE</span></span>|<span data-ttu-id="177f7-175">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-175">Int32</span></span>|  
|<span data-ttu-id="177f7-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="177f7-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="177f7-177">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-177">Int32</span></span>|  
|<span data-ttu-id="177f7-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="177f7-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="177f7-179">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-179">Int16</span></span>|  
|<span data-ttu-id="177f7-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="177f7-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="177f7-181">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-181">Int16</span></span>|  
|<span data-ttu-id="177f7-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="177f7-182">NULLABLE</span></span>|<span data-ttu-id="177f7-183">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-183">Int16</span></span>|  
|<span data-ttu-id="177f7-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-184">REMARKS</span></span>|<span data-ttu-id="177f7-185">String</span><span class="sxs-lookup"><span data-stu-id="177f7-185">String</span></span>|  
|<span data-ttu-id="177f7-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="177f7-186">COLUMN_DEF</span></span>|<span data-ttu-id="177f7-187">String</span><span class="sxs-lookup"><span data-stu-id="177f7-187">String</span></span>|  
|<span data-ttu-id="177f7-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="177f7-189">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-189">Int16</span></span>|  
|<span data-ttu-id="177f7-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="177f7-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="177f7-191">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-191">Int16</span></span>|  
|<span data-ttu-id="177f7-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="177f7-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="177f7-193">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-193">Int32</span></span>|  
|<span data-ttu-id="177f7-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="177f7-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="177f7-195">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-195">Int32</span></span>|  
|<span data-ttu-id="177f7-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="177f7-196">IS_NULLABLE</span></span>|<span data-ttu-id="177f7-197">String</span><span class="sxs-lookup"><span data-stu-id="177f7-197">String</span></span>|  
|<span data-ttu-id="177f7-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="177f7-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="177f7-199">String</span><span class="sxs-lookup"><span data-stu-id="177f7-199">String</span></span>|  
|<span data-ttu-id="177f7-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="177f7-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="177f7-201">String</span><span class="sxs-lookup"><span data-stu-id="177f7-201">String</span></span>|  
|<span data-ttu-id="177f7-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="177f7-203">Byte</span><span class="sxs-lookup"><span data-stu-id="177f7-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="177f7-204">手順</span><span class="sxs-lookup"><span data-stu-id="177f7-204">Procedures</span></span>  
  
|<span data-ttu-id="177f7-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-205">ColumnName</span></span>|<span data-ttu-id="177f7-206">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="177f7-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="177f7-208">String</span><span class="sxs-lookup"><span data-stu-id="177f7-208">String</span></span>|  
|<span data-ttu-id="177f7-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="177f7-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="177f7-210">String</span><span class="sxs-lookup"><span data-stu-id="177f7-210">String</span></span>|  
|<span data-ttu-id="177f7-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="177f7-212">String</span><span class="sxs-lookup"><span data-stu-id="177f7-212">String</span></span>|  
|<span data-ttu-id="177f7-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="177f7-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="177f7-214">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-214">Int32</span></span>|  
|<span data-ttu-id="177f7-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="177f7-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="177f7-216">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-216">Int32</span></span>|  
|<span data-ttu-id="177f7-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="177f7-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="177f7-218">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-218">Int32</span></span>|  
|<span data-ttu-id="177f7-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-219">REMARKS</span></span>|<span data-ttu-id="177f7-220">String</span><span class="sxs-lookup"><span data-stu-id="177f7-220">String</span></span>|  
|<span data-ttu-id="177f7-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="177f7-222">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="177f7-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="177f7-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="177f7-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-224">ColumnName</span></span>|<span data-ttu-id="177f7-225">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="177f7-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="177f7-227">String</span><span class="sxs-lookup"><span data-stu-id="177f7-227">String</span></span>|  
|<span data-ttu-id="177f7-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="177f7-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="177f7-229">String</span><span class="sxs-lookup"><span data-stu-id="177f7-229">String</span></span>|  
|<span data-ttu-id="177f7-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="177f7-231">String</span><span class="sxs-lookup"><span data-stu-id="177f7-231">String</span></span>|  
|<span data-ttu-id="177f7-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-232">COLUMN_NAME</span></span>|<span data-ttu-id="177f7-233">String</span><span class="sxs-lookup"><span data-stu-id="177f7-233">String</span></span>|  
|<span data-ttu-id="177f7-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-234">COLUMN_TYPE</span></span>|<span data-ttu-id="177f7-235">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-235">Int16</span></span>|  
|<span data-ttu-id="177f7-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-236">DATA_TYPE</span></span>|<span data-ttu-id="177f7-237">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-237">Int16</span></span>|  
|<span data-ttu-id="177f7-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-238">TYPE_NAME</span></span>|<span data-ttu-id="177f7-239">String</span><span class="sxs-lookup"><span data-stu-id="177f7-239">String</span></span>|  
|<span data-ttu-id="177f7-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="177f7-240">COLUMN_SIZE</span></span>|<span data-ttu-id="177f7-241">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-241">Int32</span></span>|  
|<span data-ttu-id="177f7-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="177f7-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="177f7-243">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-243">Int32</span></span>|  
|<span data-ttu-id="177f7-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="177f7-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="177f7-245">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-245">Int16</span></span>|  
|<span data-ttu-id="177f7-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="177f7-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="177f7-247">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-247">Int16</span></span>|  
|<span data-ttu-id="177f7-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="177f7-248">NULLABLE</span></span>|<span data-ttu-id="177f7-249">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-249">Int16</span></span>|  
|<span data-ttu-id="177f7-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-250">REMARKS</span></span>|<span data-ttu-id="177f7-251">String</span><span class="sxs-lookup"><span data-stu-id="177f7-251">String</span></span>|  
|<span data-ttu-id="177f7-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="177f7-252">COLUMN_DEF</span></span>|<span data-ttu-id="177f7-253">String</span><span class="sxs-lookup"><span data-stu-id="177f7-253">String</span></span>|  
|<span data-ttu-id="177f7-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="177f7-255">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-255">Int16</span></span>|  
|<span data-ttu-id="177f7-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="177f7-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="177f7-257">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-257">Int16</span></span>|  
|<span data-ttu-id="177f7-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="177f7-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="177f7-259">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-259">Int32</span></span>|  
|<span data-ttu-id="177f7-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="177f7-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="177f7-261">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-261">Int32</span></span>|  
|<span data-ttu-id="177f7-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="177f7-262">IS_NULLABLE</span></span>|<span data-ttu-id="177f7-263">String</span><span class="sxs-lookup"><span data-stu-id="177f7-263">String</span></span>|  
|<span data-ttu-id="177f7-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="177f7-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="177f7-265">String</span><span class="sxs-lookup"><span data-stu-id="177f7-265">String</span></span>|  
|<span data-ttu-id="177f7-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="177f7-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="177f7-267">String</span><span class="sxs-lookup"><span data-stu-id="177f7-267">String</span></span>|  
|<span data-ttu-id="177f7-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="177f7-269">Byte</span><span class="sxs-lookup"><span data-stu-id="177f7-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="177f7-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="177f7-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="177f7-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-271">ColumnName</span></span>|<span data-ttu-id="177f7-272">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="177f7-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="177f7-274">String</span><span class="sxs-lookup"><span data-stu-id="177f7-274">String</span></span>|  
|<span data-ttu-id="177f7-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="177f7-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="177f7-276">String</span><span class="sxs-lookup"><span data-stu-id="177f7-276">String</span></span>|  
|<span data-ttu-id="177f7-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="177f7-278">String</span><span class="sxs-lookup"><span data-stu-id="177f7-278">String</span></span>|  
|<span data-ttu-id="177f7-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-279">COLUMN_NAME</span></span>|<span data-ttu-id="177f7-280">String</span><span class="sxs-lookup"><span data-stu-id="177f7-280">String</span></span>|  
|<span data-ttu-id="177f7-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-281">COLUMN_TYPE</span></span>|<span data-ttu-id="177f7-282">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-282">Int16</span></span>|  
|<span data-ttu-id="177f7-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-283">DATA_TYPE</span></span>|<span data-ttu-id="177f7-284">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-284">Int16</span></span>|  
|<span data-ttu-id="177f7-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-285">TYPE_NAME</span></span>|<span data-ttu-id="177f7-286">String</span><span class="sxs-lookup"><span data-stu-id="177f7-286">String</span></span>|  
|<span data-ttu-id="177f7-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="177f7-287">COLUMN_SIZE</span></span>|<span data-ttu-id="177f7-288">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-288">Int32</span></span>|  
|<span data-ttu-id="177f7-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="177f7-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="177f7-290">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-290">Int32</span></span>|  
|<span data-ttu-id="177f7-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="177f7-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="177f7-292">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-292">Int16</span></span>|  
|<span data-ttu-id="177f7-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="177f7-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="177f7-294">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-294">Int16</span></span>|  
|<span data-ttu-id="177f7-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="177f7-295">NULLABLE</span></span>|<span data-ttu-id="177f7-296">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-296">Int16</span></span>|  
|<span data-ttu-id="177f7-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-297">REMARKS</span></span>|<span data-ttu-id="177f7-298">String</span><span class="sxs-lookup"><span data-stu-id="177f7-298">String</span></span>|  
|<span data-ttu-id="177f7-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="177f7-299">COLUMN_DEF</span></span>|<span data-ttu-id="177f7-300">String</span><span class="sxs-lookup"><span data-stu-id="177f7-300">String</span></span>|  
|<span data-ttu-id="177f7-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="177f7-302">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-302">Int16</span></span>|  
|<span data-ttu-id="177f7-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="177f7-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="177f7-304">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-304">Int16</span></span>|  
|<span data-ttu-id="177f7-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="177f7-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="177f7-306">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-306">Int32</span></span>|  
|<span data-ttu-id="177f7-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="177f7-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="177f7-308">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-308">Int32</span></span>|  
|<span data-ttu-id="177f7-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="177f7-309">IS_NULLABLE</span></span>|<span data-ttu-id="177f7-310">String</span><span class="sxs-lookup"><span data-stu-id="177f7-310">String</span></span>|  
|<span data-ttu-id="177f7-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="177f7-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="177f7-312">String</span><span class="sxs-lookup"><span data-stu-id="177f7-312">String</span></span>|  
|<span data-ttu-id="177f7-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="177f7-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="177f7-314">String</span><span class="sxs-lookup"><span data-stu-id="177f7-314">String</span></span>|  
|<span data-ttu-id="177f7-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="177f7-316">Byte</span><span class="sxs-lookup"><span data-stu-id="177f7-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="177f7-317">Microsoft Oracle ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="177f7-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="177f7-318">Microsoft SQL Server Oracle ODBC Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="177f7-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="177f7-319">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="177f7-319">Tables</span></span>  
  
-   <span data-ttu-id="177f7-320">列</span><span class="sxs-lookup"><span data-stu-id="177f7-320">Columns</span></span>  
  
-   <span data-ttu-id="177f7-321">手順</span><span class="sxs-lookup"><span data-stu-id="177f7-321">Procedures</span></span>  
  
-   <span data-ttu-id="177f7-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="177f7-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="177f7-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="177f7-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="177f7-324">ビュー</span><span class="sxs-lookup"><span data-stu-id="177f7-324">Views</span></span>  
  
-   <span data-ttu-id="177f7-325">Indexes</span><span class="sxs-lookup"><span data-stu-id="177f7-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="177f7-326">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="177f7-326">Tables and Views</span></span>  
  
|<span data-ttu-id="177f7-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-327">ColumnName</span></span>|<span data-ttu-id="177f7-328">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="177f7-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="177f7-330">String</span><span class="sxs-lookup"><span data-stu-id="177f7-330">String</span></span>|  
|<span data-ttu-id="177f7-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="177f7-331">TABLE_OWNER</span></span>|<span data-ttu-id="177f7-332">String</span><span class="sxs-lookup"><span data-stu-id="177f7-332">String</span></span>|  
|<span data-ttu-id="177f7-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-333">TABLE_NAME</span></span>|<span data-ttu-id="177f7-334">String</span><span class="sxs-lookup"><span data-stu-id="177f7-334">String</span></span>|  
|<span data-ttu-id="177f7-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-335">TABLE_TYPE</span></span>|<span data-ttu-id="177f7-336">String</span><span class="sxs-lookup"><span data-stu-id="177f7-336">String</span></span>|  
|<span data-ttu-id="177f7-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-337">REMARKS</span></span>|<span data-ttu-id="177f7-338">String</span><span class="sxs-lookup"><span data-stu-id="177f7-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="177f7-339">列</span><span class="sxs-lookup"><span data-stu-id="177f7-339">Columns</span></span>  
  
|<span data-ttu-id="177f7-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-340">ColumnName</span></span>|<span data-ttu-id="177f7-341">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="177f7-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="177f7-343">String</span><span class="sxs-lookup"><span data-stu-id="177f7-343">String</span></span>|  
|<span data-ttu-id="177f7-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="177f7-344">TABLE_OWNER</span></span>|<span data-ttu-id="177f7-345">String</span><span class="sxs-lookup"><span data-stu-id="177f7-345">String</span></span>|  
|<span data-ttu-id="177f7-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-346">TABLE_NAME</span></span>|<span data-ttu-id="177f7-347">String</span><span class="sxs-lookup"><span data-stu-id="177f7-347">String</span></span>|  
|<span data-ttu-id="177f7-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-348">COLUMN_NAME</span></span>|<span data-ttu-id="177f7-349">String</span><span class="sxs-lookup"><span data-stu-id="177f7-349">String</span></span>|  
|<span data-ttu-id="177f7-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-350">DATA_TYPE</span></span>|<span data-ttu-id="177f7-351">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-351">Int16</span></span>|  
|<span data-ttu-id="177f7-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-352">TYPE_NAME</span></span>|<span data-ttu-id="177f7-353">String</span><span class="sxs-lookup"><span data-stu-id="177f7-353">String</span></span>|  
|<span data-ttu-id="177f7-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="177f7-354">PRECISION</span></span>|<span data-ttu-id="177f7-355">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-355">Int32</span></span>|  
|<span data-ttu-id="177f7-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="177f7-356">LENGTH</span></span>|<span data-ttu-id="177f7-357">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-357">Int32</span></span>|  
|<span data-ttu-id="177f7-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="177f7-358">SCALE</span></span>|<span data-ttu-id="177f7-359">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-359">Int16</span></span>|  
|<span data-ttu-id="177f7-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="177f7-360">RADIX</span></span>|<span data-ttu-id="177f7-361">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-361">Int16</span></span>|  
|<span data-ttu-id="177f7-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="177f7-362">NULLABLE</span></span>|<span data-ttu-id="177f7-363">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-363">Int16</span></span>|  
|<span data-ttu-id="177f7-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-364">REMARKS</span></span>|<span data-ttu-id="177f7-365">String</span><span class="sxs-lookup"><span data-stu-id="177f7-365">String</span></span>|  
|<span data-ttu-id="177f7-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="177f7-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="177f7-367">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="177f7-368">手順</span><span class="sxs-lookup"><span data-stu-id="177f7-368">Procedures</span></span>  
  
|<span data-ttu-id="177f7-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-369">ColumnName</span></span>|<span data-ttu-id="177f7-370">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="177f7-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="177f7-372">String</span><span class="sxs-lookup"><span data-stu-id="177f7-372">String</span></span>|  
|<span data-ttu-id="177f7-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="177f7-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="177f7-374">String</span><span class="sxs-lookup"><span data-stu-id="177f7-374">String</span></span>|  
|<span data-ttu-id="177f7-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="177f7-376">String</span><span class="sxs-lookup"><span data-stu-id="177f7-376">String</span></span>|  
|<span data-ttu-id="177f7-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="177f7-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="177f7-378">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-378">Int16</span></span>|  
|<span data-ttu-id="177f7-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="177f7-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="177f7-380">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-380">Int16</span></span>|  
|<span data-ttu-id="177f7-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="177f7-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="177f7-382">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-382">Int16</span></span>|  
|<span data-ttu-id="177f7-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-383">REMARKS</span></span>|<span data-ttu-id="177f7-384">String</span><span class="sxs-lookup"><span data-stu-id="177f7-384">String</span></span>|  
|<span data-ttu-id="177f7-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="177f7-386">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="177f7-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="177f7-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="177f7-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-388">ColumnName</span></span>|<span data-ttu-id="177f7-389">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="177f7-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="177f7-391">String</span><span class="sxs-lookup"><span data-stu-id="177f7-391">String</span></span>|  
|<span data-ttu-id="177f7-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="177f7-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="177f7-393">String</span><span class="sxs-lookup"><span data-stu-id="177f7-393">String</span></span>|  
|<span data-ttu-id="177f7-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="177f7-395">String</span><span class="sxs-lookup"><span data-stu-id="177f7-395">String</span></span>|  
|<span data-ttu-id="177f7-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-396">COLUMN_NAME</span></span>|<span data-ttu-id="177f7-397">String</span><span class="sxs-lookup"><span data-stu-id="177f7-397">String</span></span>|  
|<span data-ttu-id="177f7-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-398">COLUMN_TYPE</span></span>|<span data-ttu-id="177f7-399">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-399">Int16</span></span>|  
|<span data-ttu-id="177f7-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-400">DATA_TYPE</span></span>|<span data-ttu-id="177f7-401">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-401">Int16</span></span>|  
|<span data-ttu-id="177f7-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-402">TYPE_NAME</span></span>|<span data-ttu-id="177f7-403">String</span><span class="sxs-lookup"><span data-stu-id="177f7-403">String</span></span>|  
|<span data-ttu-id="177f7-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="177f7-404">PRECISION</span></span>|<span data-ttu-id="177f7-405">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-405">Int32</span></span>|  
|<span data-ttu-id="177f7-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="177f7-406">LENGTH</span></span>|<span data-ttu-id="177f7-407">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-407">Int32</span></span>|  
|<span data-ttu-id="177f7-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="177f7-408">SCALE</span></span>|<span data-ttu-id="177f7-409">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-409">Int16</span></span>|  
|<span data-ttu-id="177f7-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="177f7-410">RADIX</span></span>|<span data-ttu-id="177f7-411">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-411">Int16</span></span>|  
|<span data-ttu-id="177f7-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="177f7-412">NULLABLE</span></span>|<span data-ttu-id="177f7-413">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-413">Int16</span></span>|  
|<span data-ttu-id="177f7-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-414">REMARKS</span></span>|<span data-ttu-id="177f7-415">String</span><span class="sxs-lookup"><span data-stu-id="177f7-415">String</span></span>|  
|<span data-ttu-id="177f7-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="177f7-416">OVERLOAD</span></span>|<span data-ttu-id="177f7-417">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-417">Int32</span></span>|  
|<span data-ttu-id="177f7-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="177f7-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="177f7-419">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="177f7-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="177f7-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="177f7-421">Microsoft Jet ODBC Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="177f7-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="177f7-422">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="177f7-422">Tables</span></span>  
  
-   <span data-ttu-id="177f7-423">Indexes</span><span class="sxs-lookup"><span data-stu-id="177f7-423">Indexes</span></span>  
  
-   <span data-ttu-id="177f7-424">列</span><span class="sxs-lookup"><span data-stu-id="177f7-424">Columns</span></span>  
  
-   <span data-ttu-id="177f7-425">手順</span><span class="sxs-lookup"><span data-stu-id="177f7-425">Procedures</span></span>  
  
-   <span data-ttu-id="177f7-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="177f7-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="177f7-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="177f7-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="177f7-428">ビュー</span><span class="sxs-lookup"><span data-stu-id="177f7-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="177f7-429">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="177f7-429">Tables and Views</span></span>  
  
|<span data-ttu-id="177f7-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-430">ColumnName</span></span>|<span data-ttu-id="177f7-431">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="177f7-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="177f7-433">String</span><span class="sxs-lookup"><span data-stu-id="177f7-433">String</span></span>|  
|<span data-ttu-id="177f7-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="177f7-434">TABLE_OWNER</span></span>|<span data-ttu-id="177f7-435">String</span><span class="sxs-lookup"><span data-stu-id="177f7-435">String</span></span>|  
|<span data-ttu-id="177f7-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-436">TABLE_NAME</span></span>|<span data-ttu-id="177f7-437">String</span><span class="sxs-lookup"><span data-stu-id="177f7-437">String</span></span>|  
|<span data-ttu-id="177f7-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-438">TABLE_TYPE</span></span>|<span data-ttu-id="177f7-439">String</span><span class="sxs-lookup"><span data-stu-id="177f7-439">String</span></span>|  
|<span data-ttu-id="177f7-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-440">REMARKS</span></span>|<span data-ttu-id="177f7-441">String</span><span class="sxs-lookup"><span data-stu-id="177f7-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="177f7-442">列</span><span class="sxs-lookup"><span data-stu-id="177f7-442">Columns</span></span>  
  
|<span data-ttu-id="177f7-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-443">ColumnName</span></span>|<span data-ttu-id="177f7-444">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="177f7-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="177f7-446">String</span><span class="sxs-lookup"><span data-stu-id="177f7-446">String</span></span>|  
|<span data-ttu-id="177f7-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="177f7-447">TABLE_OWNER</span></span>|<span data-ttu-id="177f7-448">String</span><span class="sxs-lookup"><span data-stu-id="177f7-448">String</span></span>|  
|<span data-ttu-id="177f7-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-449">TABLE_NAME</span></span>|<span data-ttu-id="177f7-450">String</span><span class="sxs-lookup"><span data-stu-id="177f7-450">String</span></span>|  
|<span data-ttu-id="177f7-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-451">COLUMN_NAME</span></span>|<span data-ttu-id="177f7-452">String</span><span class="sxs-lookup"><span data-stu-id="177f7-452">String</span></span>|  
|<span data-ttu-id="177f7-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-453">DATA_TYPE</span></span>|<span data-ttu-id="177f7-454">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-454">Int16</span></span>|  
|<span data-ttu-id="177f7-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-455">TYPE_NAME</span></span>|<span data-ttu-id="177f7-456">String</span><span class="sxs-lookup"><span data-stu-id="177f7-456">String</span></span>|  
|<span data-ttu-id="177f7-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="177f7-457">PRECISION</span></span>|<span data-ttu-id="177f7-458">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-458">Int32</span></span>|  
|<span data-ttu-id="177f7-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="177f7-459">LENGTH</span></span>|<span data-ttu-id="177f7-460">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-460">Int32</span></span>|  
|<span data-ttu-id="177f7-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="177f7-461">SCALE</span></span>|<span data-ttu-id="177f7-462">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-462">Int16</span></span>|  
|<span data-ttu-id="177f7-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="177f7-463">RADIX</span></span>|<span data-ttu-id="177f7-464">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-464">Int16</span></span>|  
|<span data-ttu-id="177f7-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="177f7-465">NULLABLE</span></span>|<span data-ttu-id="177f7-466">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-466">Int16</span></span>|  
|<span data-ttu-id="177f7-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-467">REMARKS</span></span>|<span data-ttu-id="177f7-468">String</span><span class="sxs-lookup"><span data-stu-id="177f7-468">String</span></span>|  
|<span data-ttu-id="177f7-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="177f7-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="177f7-470">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="177f7-471">手順</span><span class="sxs-lookup"><span data-stu-id="177f7-471">Procedures</span></span>  
  
|<span data-ttu-id="177f7-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-472">ColumnName</span></span>|<span data-ttu-id="177f7-473">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="177f7-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="177f7-475">String</span><span class="sxs-lookup"><span data-stu-id="177f7-475">String</span></span>|  
|<span data-ttu-id="177f7-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="177f7-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="177f7-477">String</span><span class="sxs-lookup"><span data-stu-id="177f7-477">String</span></span>|  
|<span data-ttu-id="177f7-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="177f7-479">String</span><span class="sxs-lookup"><span data-stu-id="177f7-479">String</span></span>|  
|<span data-ttu-id="177f7-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="177f7-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="177f7-481">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-481">Int16</span></span>|  
|<span data-ttu-id="177f7-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="177f7-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="177f7-483">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-483">Int16</span></span>|  
|<span data-ttu-id="177f7-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="177f7-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="177f7-485">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-485">Int16</span></span>|  
|<span data-ttu-id="177f7-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-486">REMARKS</span></span>|<span data-ttu-id="177f7-487">String</span><span class="sxs-lookup"><span data-stu-id="177f7-487">String</span></span>|  
|<span data-ttu-id="177f7-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="177f7-489">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="177f7-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="177f7-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="177f7-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-491">ColumnName</span></span>|<span data-ttu-id="177f7-492">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="177f7-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="177f7-494">String</span><span class="sxs-lookup"><span data-stu-id="177f7-494">String</span></span>|  
|<span data-ttu-id="177f7-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="177f7-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="177f7-496">String</span><span class="sxs-lookup"><span data-stu-id="177f7-496">String</span></span>|  
|<span data-ttu-id="177f7-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="177f7-498">String</span><span class="sxs-lookup"><span data-stu-id="177f7-498">String</span></span>|  
|<span data-ttu-id="177f7-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-499">COLUMN_NAME</span></span>|<span data-ttu-id="177f7-500">String</span><span class="sxs-lookup"><span data-stu-id="177f7-500">String</span></span>|  
|<span data-ttu-id="177f7-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-501">COLUMN_TYPE</span></span>|<span data-ttu-id="177f7-502">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-502">Int16</span></span>|  
|<span data-ttu-id="177f7-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-503">DATA_TYPE</span></span>|<span data-ttu-id="177f7-504">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-504">Int16</span></span>|  
|<span data-ttu-id="177f7-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-505">TYPE_NAME</span></span>|<span data-ttu-id="177f7-506">String</span><span class="sxs-lookup"><span data-stu-id="177f7-506">String</span></span>|  
|<span data-ttu-id="177f7-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="177f7-507">PRECISION</span></span>|<span data-ttu-id="177f7-508">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-508">Int32</span></span>|  
|<span data-ttu-id="177f7-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="177f7-509">LENGTH</span></span>|<span data-ttu-id="177f7-510">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-510">Int32</span></span>|  
|<span data-ttu-id="177f7-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="177f7-511">SCALE</span></span>|<span data-ttu-id="177f7-512">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-512">Int16</span></span>|  
|<span data-ttu-id="177f7-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="177f7-513">RADIX</span></span>|<span data-ttu-id="177f7-514">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-514">Int16</span></span>|  
|<span data-ttu-id="177f7-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="177f7-515">NULLABLE</span></span>|<span data-ttu-id="177f7-516">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-516">Int16</span></span>|  
|<span data-ttu-id="177f7-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-517">REMARKS</span></span>|<span data-ttu-id="177f7-518">String</span><span class="sxs-lookup"><span data-stu-id="177f7-518">String</span></span>|  
|<span data-ttu-id="177f7-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="177f7-519">OVERLOAD</span></span>|<span data-ttu-id="177f7-520">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-520">Int32</span></span>|  
|<span data-ttu-id="177f7-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="177f7-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="177f7-522">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="177f7-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="177f7-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="177f7-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="177f7-524">ColumnName</span></span>|<span data-ttu-id="177f7-525">DataType</span><span class="sxs-lookup"><span data-stu-id="177f7-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="177f7-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="177f7-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="177f7-527">String</span><span class="sxs-lookup"><span data-stu-id="177f7-527">String</span></span>|  
|<span data-ttu-id="177f7-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="177f7-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="177f7-529">String</span><span class="sxs-lookup"><span data-stu-id="177f7-529">String</span></span>|  
|<span data-ttu-id="177f7-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="177f7-531">String</span><span class="sxs-lookup"><span data-stu-id="177f7-531">String</span></span>|  
|<span data-ttu-id="177f7-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-532">COLUMN_NAME</span></span>|<span data-ttu-id="177f7-533">String</span><span class="sxs-lookup"><span data-stu-id="177f7-533">String</span></span>|  
|<span data-ttu-id="177f7-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-534">COLUMN_TYPE</span></span>|<span data-ttu-id="177f7-535">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-535">Int16</span></span>|  
|<span data-ttu-id="177f7-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-536">DATA_TYPE</span></span>|<span data-ttu-id="177f7-537">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-537">Int16</span></span>|  
|<span data-ttu-id="177f7-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="177f7-538">TYPE_NAME</span></span>|<span data-ttu-id="177f7-539">String</span><span class="sxs-lookup"><span data-stu-id="177f7-539">String</span></span>|  
|<span data-ttu-id="177f7-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="177f7-540">COLUMN_SIZE</span></span>|<span data-ttu-id="177f7-541">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-541">Int32</span></span>|  
|<span data-ttu-id="177f7-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="177f7-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="177f7-543">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-543">Int32</span></span>|  
|<span data-ttu-id="177f7-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="177f7-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="177f7-545">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-545">Int16</span></span>|  
|<span data-ttu-id="177f7-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="177f7-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="177f7-547">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-547">Int16</span></span>|  
|<span data-ttu-id="177f7-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="177f7-548">NULLABLE</span></span>|<span data-ttu-id="177f7-549">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-549">Int16</span></span>|  
|<span data-ttu-id="177f7-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="177f7-550">REMARKS</span></span>|<span data-ttu-id="177f7-551">String</span><span class="sxs-lookup"><span data-stu-id="177f7-551">String</span></span>|  
|<span data-ttu-id="177f7-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="177f7-552">COLUMN_DEF</span></span>|<span data-ttu-id="177f7-553">String</span><span class="sxs-lookup"><span data-stu-id="177f7-553">String</span></span>|  
|<span data-ttu-id="177f7-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="177f7-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="177f7-555">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-555">Int16</span></span>|  
|<span data-ttu-id="177f7-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="177f7-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="177f7-557">Int16</span><span class="sxs-lookup"><span data-stu-id="177f7-557">Int16</span></span>|  
|<span data-ttu-id="177f7-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="177f7-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="177f7-559">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-559">Int32</span></span>|  
|<span data-ttu-id="177f7-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="177f7-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="177f7-561">Int32</span><span class="sxs-lookup"><span data-stu-id="177f7-561">Int32</span></span>|  
|<span data-ttu-id="177f7-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="177f7-562">IS_NULLABLE</span></span>|<span data-ttu-id="177f7-563">String</span><span class="sxs-lookup"><span data-stu-id="177f7-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="177f7-564">関連項目</span><span class="sxs-lookup"><span data-stu-id="177f7-564">See Also</span></span>  
 [<span data-ttu-id="177f7-565">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="177f7-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
