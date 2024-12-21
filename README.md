# Geospatial Network Indexing and Spatial Query Optimization

## Overview
This project implements an in-memory spatial network index structure for efficient management and querying of large-scale geospatial networks. The implementation follows the framework presented in [this VLDB paper](https://www.vldb.org/conf/2003/papers/S24P02.pdf) and includes implementations of spatial nearest neighbor queries using both Incremental Euclidean Restriction (IER) and Incremental Network Expansion (INE) methods.

## Features
- In-memory spatial network indexing structure
- R-tree indexing for POI data
- Network Storage Scheme with three components:
  - Adjacency component for network connectivity
  - Poly-line component for segment representation
  - R-tree index for polylines
- Implementation of two spatial nearest neighbor query methods:
  - Incremental Euclidean Restriction (IER)
  - Incremental Network Expansion (INE)
- Performance comparison between IER and INE algorithms

## Implementation Details

### Data Structure
The implementation consists of several key components:
- POI R-tree index for efficient point-of-interest queries
- Network storage scheme including:
  - Node adjacency lists
  - Polyline storage
  - Network R-tree index

### Key Algorithms
1. **Primitive Functions**:
   - `check_entity(seg, p, dT)`: Check if POI lies on/near segment
   - `find_segment(p)`: Find road segment covering point p
   - `find_entities(seg)`: Find POIs near segment
   - `compute_ND(p1, p2)`: Compute network distance between points

2. **KNN Search Algorithms**:
   - IER (Incremental Euclidean Restriction)
   - INE (Incremental Network Expansion)

## Dependencies
- geopandas
- osmnx
- rtree
- networkx
- pandas
- shapely

## Performance Analysis
The implementation includes a comprehensive performance analysis comparing IER and INE algorithms across different k values (k = 1, 5, 10, 15, 20). Key findings include:
- INE generally performs better than IER for larger k values
- IER may perform better for k=1 in cases where Euclidean distance is a good estimate for network distance
- Performance difference between algorithms increases with k

## Usage
The project is implemented as a Jupyter notebook with clear sections for:
1. Data downloading and preprocessing
2. Index creation
3. Implementation of primitive functions
4. KNN search algorithms
5. Performance analysis

## Dataset
The implementation uses San Francisco road network and POI data:
- Road network data obtained via OSMnx
- POI data includes tourist attractions and amenities
- Data is preprocessed to ensure POIs fall within the road network bounds

## Challenges and Considerations
- Buffer distance (dT) parameter requires fine-tuning based on network characteristics
- Trade-offs between query accuracy and performance
- Memory management for large-scale networks

## Future Improvements
- Parameter optimization for different network types
- Implementation of caching mechanisms
- Support for dynamic network updates
- Additional query types and optimization strategies

## Author
Omar Alkhadra
