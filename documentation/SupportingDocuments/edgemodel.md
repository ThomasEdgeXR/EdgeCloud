```mermaid
erDiagram
    APPLICATION_CLIENT }|--|| APPLICATION_INSTANCE : exchanges_userdata
    APPLICATION_INSTANCE  }|--|| APPLICATION_EDGE_PART : is_instantiated_of
    APPLICATION_BACKEND_PART o{--|| APPLICATION_CLIENT : exchanges_userdata
    APPLICATION_INSTANCE }|--o{ APPLICATION_BACKEND_PART : exchanges_userdata
    APPLICATION_INSTANCE{
        string service_endpoint
    }
    APPLICATION_SERVICE_PROVIDER ||--|{ APPLICATION_CLIENT: provides
    APPLICATION_SERVICE_PROVIDER ||--|{ APPLICATION_EDGE_PART: onboards
    APPLICATION_EDGE_PART{
        string flavor
    }
    APPLICATION_SERVICE_PROVIDER ||--o{ APPLICATION_BACKEND_PART: provides
    APPLICATION_INSTANCE  }|--|| CLOUDLET : is_deployed_on
    CLOUDLET {
        string TSP
        string compute_resources
        string network_resources
        string location
        string region
    }
    MEC_PLATFORM ||--|| CLOUDLET : is_same_as
    EDGE_CLOUD ||--|{ MEC_PLATFORM : is_a_collection_of
    EDGE_APPLICATION ||--|{ APPLICATION_EDGE_PART : includes
    UE ||--|{ APPLICATION_CLIENT : is_running
    UE ||..|| USER_CLIENT : is_running
    UE {
        string ue_identity
    }
    USER_CLIENT  }|--|| OPERATOR_PLATFORM : communicate
