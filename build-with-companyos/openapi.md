# OpenAPI reference

This page is generated from `docs/contracts/action-platform-openapi.json`.

```json
{
  "openapi": "3.1.0",
  "info": {
    "title": "CompanyOS Action Platform API",
    "version": "1.0.0",
    "description": "Canonical HTTP interface for action execution and canonical error envelopes."
  },
  "paths": {
    "/api/v1/operations": {
      "get": {
        "summary": "List available action operations",
        "responses": {
          "200": {
            "description": "Available action operations",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "required": [
                    "operations"
                  ],
                  "properties": {
                    "operations": {
                      "type": "array",
                      "items": {
                        "type": "object",
                        "required": [
                          "id",
                          "title",
                          "description",
                          "inputSchema",
                          "outputSchema",
                          "availability",
                          "errors"
                        ],
                        "properties": {
                          "id": {
                            "type": "string",
                            "enum": [
                              "knowledge.list_visible_files",
                              "m365.list_authorized_senders",
                              "m365.list_send_history",
                              "m365.send_email",
                              "procedures.create_draft",
                              "record_store.archive_collection",
                              "record_store.archive_record",
                              "record_store.create_collection",
                              "record_store.get_record",
                              "record_store.get_record_history",
                              "record_store.list_records",
                              "record_store.patch_record",
                              "record_store.permanently_delete_collection",
                              "record_store.permanently_delete_record",
                              "record_store.push_record",
                              "record_store.replace_record",
                              "record_store.restore_collection",
                              "record_store.restore_record"
                            ]
                          },
                          "title": {
                            "type": "string"
                          },
                          "description": {
                            "type": "string"
                          },
                          "inputSchema": {
                            "type": "object"
                          },
                          "outputSchema": {
                            "type": "object"
                          },
                          "availability": {
                            "type": "string",
                            "enum": [
                              "workspace_member",
                              "owner_workspace"
                            ]
                          },
                          "errors": {
                            "type": "array",
                            "items": {
                              "$ref": "#/components/schemas/ActionErrorTemplate"
                            }
                          },
                          "deprecation": {
                            "type": "object",
                            "required": [
                              "deprecatedAt",
                              "sunsetAt"
                            ],
                            "properties": {
                              "deprecatedAt": {
                                "type": "string",
                                "format": "date-time"
                              },
                              "sunsetAt": {
                                "type": "string",
                                "format": "date-time"
                              },
                              "migration": {
                                "type": "object",
                                "properties": {
                                  "operationId": {
                                    "type": "string"
                                  },
                                  "note": {
                                    "type": "string"
                                  }
                                }
                              }
                            }
                          }
                        },
                        "additionalProperties": false
                      }
                    }
                  }
                }
              }
            }
          },
          "401": {
            "description": "Action Platform authentication is required",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/ActionErrorEnvelope"
                }
              }
            }
          },
          "403": {
            "description": "An active Workspace membership is required",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/ActionErrorEnvelope"
                }
              }
            }
          }
        }
      }
    },
    "/api/v1/operations/{operationId}": {
      "post": {
        "summary": "Execute action operation",
        "parameters": [
          {
            "name": "operationId",
            "in": "path",
            "required": true,
            "schema": {
              "type": "string",
              "enum": [
                "knowledge.list_visible_files",
                "m365.list_authorized_senders",
                "m365.list_send_history",
                "m365.send_email",
                "procedures.create_draft",
                "record_store.archive_collection",
                "record_store.archive_record",
                "record_store.create_collection",
                "record_store.get_record",
                "record_store.get_record_history",
                "record_store.list_records",
                "record_store.patch_record",
                "record_store.permanently_delete_collection",
                "record_store.permanently_delete_record",
                "record_store.push_record",
                "record_store.replace_record",
                "record_store.restore_collection",
                "record_store.restore_record"
              ]
            }
          }
        ],
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "oneOf": [
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_knowledge_list_visible_files"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_procedures_create_draft"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_record_store_create_collection"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_record_store_push_record"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_record_store_get_record"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_record_store_list_records"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_record_store_replace_record"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_record_store_patch_record"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_record_store_get_record_history"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_record_store_archive_record"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_record_store_restore_record"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_record_store_permanently_delete_record"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_record_store_archive_collection"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_record_store_restore_collection"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_record_store_permanently_delete_collection"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_m365_list_authorized_senders"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_m365_list_send_history"
                  },
                  {
                    "$ref": "#/components/schemas/ActionPlatformOperationRequest_m365_send_email"
                  }
                ]
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Operation result envelope",
            "content": {
              "application/json": {
                "schema": {
                  "oneOf": [
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_knowledge_list_visible_files"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_procedures_create_draft"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_record_store_create_collection"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_record_store_push_record"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_record_store_get_record"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_record_store_list_records"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_record_store_replace_record"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_record_store_patch_record"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_record_store_get_record_history"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_record_store_archive_record"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_record_store_restore_record"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_record_store_permanently_delete_record"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_record_store_archive_collection"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_record_store_restore_collection"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_record_store_permanently_delete_collection"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_m365_list_authorized_senders"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_m365_list_send_history"
                    },
                    {
                      "$ref": "#/components/schemas/ActionPlatformOperationResponse_m365_send_email"
                    }
                  ]
                }
              }
            }
          },
          "400": {
            "description": "Action request validation or execution error",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/ActionErrorEnvelope"
                }
              }
            }
          },
          "401": {
            "description": "Action Platform authentication is required",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/ActionErrorEnvelope"
                }
              }
            }
          },
          "403": {
            "description": "Operation unavailable for this caller",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/ActionErrorEnvelope"
                }
              }
            }
          },
          "404": {
            "description": "Unknown operation",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/ActionErrorEnvelope"
                }
              }
            }
          },
          "502": {
            "description": "Action infrastructure failure",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/ActionErrorEnvelope"
                }
              }
            }
          },
          "503": {
            "description": "Action Platform is unavailable",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/ActionErrorEnvelope"
                }
              }
            }
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "ActionErrorTemplate": {
        "type": "object",
        "additionalProperties": false,
        "required": [
          "code",
          "message",
          "recoverable",
          "next",
          "docs_url"
        ],
        "properties": {
          "code": {
            "type": "string"
          },
          "message": {
            "type": "string"
          },
          "recoverable": {
            "type": "boolean"
          },
          "next": {
            "type": "string"
          },
          "docs_url": {
            "type": "string",
            "format": "uri-reference"
          }
        }
      },
      "ActionError": {
        "type": "object",
        "additionalProperties": false,
        "required": [
          "code",
          "message",
          "recoverable",
          "next",
          "requestId",
          "docs_url"
        ],
        "properties": {
          "code": {
            "type": "string"
          },
          "message": {
            "type": "string"
          },
          "recoverable": {
            "type": "boolean"
          },
          "next": {
            "type": "string"
          },
          "requestId": {
            "type": "string"
          },
          "docs_url": {
            "type": "string",
            "format": "uri-reference"
          }
        }
      },
      "ActionErrorEnvelope": {
        "type": "object",
        "required": [
          "error"
        ],
        "additionalProperties": false,
        "properties": {
          "error": {
            "$ref": "#/components/schemas/ActionError"
          }
        }
      },
      "ActionPlatformOperationRequest_knowledge_list_visible_files": {
        "type": "object",
        "properties": {
          "scope": {
            "type": "string",
            "enum": [
              "company",
              "personal",
              "all"
            ],
            "description": "Defaults to all."
          }
        },
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_knowledge_list_visible_files": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "groups": {
                "type": "array",
                "items": {
                  "type": "object",
                  "properties": {
                    "label": {
                      "type": "string",
                      "enum": [
                        "Company Files",
                        "Personal Files"
                      ]
                    },
                    "files": {
                      "type": "array",
                      "items": {
                        "type": "object",
                        "properties": {
                          "key": {
                            "type": "string"
                          },
                          "path": {
                            "type": "string"
                          }
                        },
                        "required": [
                          "key",
                          "path"
                        ],
                        "additionalProperties": false
                      }
                    }
                  },
                  "required": [
                    "label",
                    "files"
                  ],
                  "additionalProperties": false
                }
              }
            },
            "required": [
              "groups"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_procedures_create_draft": {
        "type": "object",
        "properties": {
          "slug": {
            "type": "string"
          },
          "title": {
            "type": "string"
          },
          "description": {
            "type": "string"
          },
          "markdown": {
            "type": "string"
          }
        },
        "required": [
          "slug",
          "title",
          "description",
          "markdown"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_procedures_create_draft": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "procedure": {
                "type": "object",
                "properties": {
                  "slug": {
                    "type": "string"
                  },
                  "title": {
                    "type": "string"
                  },
                  "description": {
                    "type": "string"
                  },
                  "state": {
                    "type": "string",
                    "enum": [
                      "draft"
                    ]
                  },
                  "type": {
                    "type": "string",
                    "enum": [
                      "procedure"
                    ]
                  },
                  "markdown": {
                    "type": "string"
                  },
                  "managedBy": {
                    "type": "string",
                    "enum": [
                      "owner"
                    ]
                  }
                },
                "required": [
                  "slug",
                  "title",
                  "description",
                  "markdown",
                  "state",
                  "type",
                  "managedBy"
                ]
              }
            },
            "required": [
              "procedure"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_record_store_create_collection": {
        "type": "object",
        "properties": {
          "name": {
            "type": "string"
          },
          "description": {
            "type": "string"
          },
          "member_writes_enabled": {
            "type": "boolean"
          }
        },
        "required": [
          "name"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_record_store_create_collection": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "collection": {
                "type": "object",
                "properties": {
                  "id": {
                    "type": "string"
                  },
                  "name": {
                    "type": "string"
                  },
                  "description": {
                    "type": "string"
                  },
                  "member_writes_enabled": {
                    "type": "boolean"
                  },
                  "state": {
                    "type": "string",
                    "enum": [
                      "active",
                      "archived"
                    ]
                  }
                },
                "required": [
                  "id",
                  "name",
                  "description",
                  "member_writes_enabled",
                  "state"
                ],
                "additionalProperties": false
              }
            },
            "required": [
              "collection"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_record_store_push_record": {
        "type": "object",
        "properties": {
          "collection_id": {
            "type": "string"
          },
          "payload": {
            "type": "object"
          },
          "idempotency_key": {
            "type": "string"
          }
        },
        "required": [
          "collection_id",
          "payload"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_record_store_push_record": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "record": {
                "type": "object",
                "properties": {
                  "id": {
                    "type": "string"
                  },
                  "collection_id": {
                    "type": "string"
                  },
                  "payload": {
                    "type": "object"
                  },
                  "version": {
                    "type": "integer"
                  },
                  "created_at": {
                    "type": "string"
                  },
                  "updated_at": {
                    "type": "string"
                  },
                  "created_by": {
                    "type": "string"
                  },
                  "updated_by": {
                    "type": "string"
                  }
                },
                "required": [
                  "id",
                  "collection_id",
                  "payload",
                  "version",
                  "created_at",
                  "updated_at",
                  "created_by",
                  "updated_by"
                ],
                "additionalProperties": false
              }
            },
            "required": [
              "record"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_record_store_get_record": {
        "type": "object",
        "properties": {
          "collection_id": {
            "type": "string"
          },
          "record_id": {
            "type": "string"
          }
        },
        "required": [
          "collection_id",
          "record_id"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_record_store_get_record": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "record": {
                "type": "object",
                "properties": {
                  "id": {
                    "type": "string"
                  },
                  "collection_id": {
                    "type": "string"
                  },
                  "payload": {
                    "type": "object"
                  },
                  "version": {
                    "type": "integer"
                  },
                  "created_at": {
                    "type": "string"
                  },
                  "updated_at": {
                    "type": "string"
                  },
                  "created_by": {
                    "type": "string"
                  },
                  "updated_by": {
                    "type": "string"
                  }
                },
                "required": [
                  "id",
                  "collection_id",
                  "payload",
                  "version",
                  "created_at",
                  "updated_at",
                  "created_by",
                  "updated_by"
                ],
                "additionalProperties": false
              }
            },
            "required": [
              "record"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_record_store_list_records": {
        "type": "object",
        "properties": {
          "collection_id": {
            "type": "string"
          },
          "cursor": {
            "type": "string"
          },
          "page_size": {
            "type": "integer",
            "minimum": 1,
            "maximum": 100
          }
        },
        "required": [
          "collection_id"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_record_store_list_records": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "records": {
                "type": "array",
                "items": {
                  "type": "object",
                  "properties": {
                    "id": {
                      "type": "string"
                    },
                    "collection_id": {
                      "type": "string"
                    },
                    "payload": {
                      "type": "object"
                    },
                    "version": {
                      "type": "integer"
                    },
                    "created_at": {
                      "type": "string"
                    },
                    "updated_at": {
                      "type": "string"
                    },
                    "created_by": {
                      "type": "string"
                    },
                    "updated_by": {
                      "type": "string"
                    }
                  },
                  "required": [
                    "id",
                    "collection_id",
                    "payload",
                    "version",
                    "created_at",
                    "updated_at",
                    "created_by",
                    "updated_by"
                  ],
                  "additionalProperties": false
                }
              },
              "next_cursor": {
                "type": "string"
              }
            },
            "required": [
              "records"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_record_store_replace_record": {
        "type": "object",
        "properties": {
          "collection_id": {
            "type": "string"
          },
          "record_id": {
            "type": "string"
          },
          "expected_version": {
            "type": "integer",
            "minimum": 1
          },
          "payload": {
            "type": "object"
          }
        },
        "required": [
          "collection_id",
          "record_id",
          "expected_version",
          "payload"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_record_store_replace_record": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "record": {
                "type": "object",
                "properties": {
                  "id": {
                    "type": "string"
                  },
                  "collection_id": {
                    "type": "string"
                  },
                  "payload": {
                    "type": "object"
                  },
                  "version": {
                    "type": "integer"
                  },
                  "created_at": {
                    "type": "string"
                  },
                  "updated_at": {
                    "type": "string"
                  },
                  "created_by": {
                    "type": "string"
                  },
                  "updated_by": {
                    "type": "string"
                  }
                },
                "required": [
                  "id",
                  "collection_id",
                  "payload",
                  "version",
                  "created_at",
                  "updated_at",
                  "created_by",
                  "updated_by"
                ],
                "additionalProperties": false
              }
            },
            "required": [
              "record"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_record_store_patch_record": {
        "type": "object",
        "properties": {
          "collection_id": {
            "type": "string"
          },
          "record_id": {
            "type": "string"
          },
          "expected_version": {
            "type": "integer",
            "minimum": 1
          },
          "patch": {
            "type": "object"
          }
        },
        "required": [
          "collection_id",
          "record_id",
          "expected_version",
          "patch"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_record_store_patch_record": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "record": {
                "type": "object",
                "properties": {
                  "id": {
                    "type": "string"
                  },
                  "collection_id": {
                    "type": "string"
                  },
                  "payload": {
                    "type": "object"
                  },
                  "version": {
                    "type": "integer"
                  },
                  "created_at": {
                    "type": "string"
                  },
                  "updated_at": {
                    "type": "string"
                  },
                  "created_by": {
                    "type": "string"
                  },
                  "updated_by": {
                    "type": "string"
                  }
                },
                "required": [
                  "id",
                  "collection_id",
                  "payload",
                  "version",
                  "created_at",
                  "updated_at",
                  "created_by",
                  "updated_by"
                ],
                "additionalProperties": false
              }
            },
            "required": [
              "record"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_record_store_get_record_history": {
        "type": "object",
        "properties": {
          "collection_id": {
            "type": "string"
          },
          "record_id": {
            "type": "string"
          }
        },
        "required": [
          "collection_id",
          "record_id"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_record_store_get_record_history": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "revisions": {
                "type": "array",
                "items": {
                  "type": "object",
                  "properties": {
                    "version": {
                      "type": "integer"
                    },
                    "payload": {
                      "type": "object"
                    },
                    "created_at": {
                      "type": "string"
                    },
                    "created_by": {
                      "type": "string"
                    }
                  },
                  "required": [
                    "version",
                    "payload",
                    "created_at",
                    "created_by"
                  ],
                  "additionalProperties": false
                }
              }
            },
            "required": [
              "revisions"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_record_store_archive_record": {
        "type": "object",
        "properties": {
          "collection_id": {
            "type": "string"
          },
          "record_id": {
            "type": "string"
          },
          "expected_version": {
            "type": "integer",
            "minimum": 1
          }
        },
        "required": [
          "collection_id",
          "record_id",
          "expected_version"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_record_store_archive_record": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "record": {
                "type": "object",
                "properties": {
                  "id": {
                    "type": "string"
                  },
                  "collection_id": {
                    "type": "string"
                  },
                  "payload": {
                    "type": "object"
                  },
                  "version": {
                    "type": "integer"
                  },
                  "created_at": {
                    "type": "string"
                  },
                  "updated_at": {
                    "type": "string"
                  },
                  "created_by": {
                    "type": "string"
                  },
                  "updated_by": {
                    "type": "string"
                  }
                },
                "required": [
                  "id",
                  "collection_id",
                  "payload",
                  "version",
                  "created_at",
                  "updated_at",
                  "created_by",
                  "updated_by"
                ],
                "additionalProperties": false
              }
            },
            "required": [
              "record"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_record_store_restore_record": {
        "type": "object",
        "properties": {
          "collection_id": {
            "type": "string"
          },
          "record_id": {
            "type": "string"
          },
          "expected_version": {
            "type": "integer",
            "minimum": 1
          }
        },
        "required": [
          "collection_id",
          "record_id",
          "expected_version"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_record_store_restore_record": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "record": {
                "type": "object",
                "properties": {
                  "id": {
                    "type": "string"
                  },
                  "collection_id": {
                    "type": "string"
                  },
                  "payload": {
                    "type": "object"
                  },
                  "version": {
                    "type": "integer"
                  },
                  "created_at": {
                    "type": "string"
                  },
                  "updated_at": {
                    "type": "string"
                  },
                  "created_by": {
                    "type": "string"
                  },
                  "updated_by": {
                    "type": "string"
                  }
                },
                "required": [
                  "id",
                  "collection_id",
                  "payload",
                  "version",
                  "created_at",
                  "updated_at",
                  "created_by",
                  "updated_by"
                ],
                "additionalProperties": false
              }
            },
            "required": [
              "record"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_record_store_permanently_delete_record": {
        "type": "object",
        "properties": {
          "collection_id": {
            "type": "string"
          },
          "record_id": {
            "type": "string"
          }
        },
        "required": [
          "collection_id",
          "record_id"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_record_store_permanently_delete_record": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "deleted": {
                "type": "boolean",
                "const": true
              },
              "collection_id": {
                "type": "string"
              },
              "record_id": {
                "type": "string"
              }
            },
            "required": [
              "deleted",
              "collection_id",
              "record_id"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_record_store_archive_collection": {
        "type": "object",
        "properties": {
          "collection_id": {
            "type": "string"
          }
        },
        "required": [
          "collection_id"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_record_store_archive_collection": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "collection": {
                "type": "object",
                "properties": {
                  "id": {
                    "type": "string"
                  },
                  "name": {
                    "type": "string"
                  },
                  "description": {
                    "type": "string"
                  },
                  "member_writes_enabled": {
                    "type": "boolean"
                  },
                  "state": {
                    "type": "string",
                    "enum": [
                      "active",
                      "archived"
                    ]
                  }
                },
                "required": [
                  "id",
                  "name",
                  "description",
                  "member_writes_enabled",
                  "state"
                ],
                "additionalProperties": false
              }
            },
            "required": [
              "collection"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_record_store_restore_collection": {
        "type": "object",
        "properties": {
          "collection_id": {
            "type": "string"
          }
        },
        "required": [
          "collection_id"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_record_store_restore_collection": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "collection": {
                "type": "object",
                "properties": {
                  "id": {
                    "type": "string"
                  },
                  "name": {
                    "type": "string"
                  },
                  "description": {
                    "type": "string"
                  },
                  "member_writes_enabled": {
                    "type": "boolean"
                  },
                  "state": {
                    "type": "string",
                    "enum": [
                      "active",
                      "archived"
                    ]
                  }
                },
                "required": [
                  "id",
                  "name",
                  "description",
                  "member_writes_enabled",
                  "state"
                ],
                "additionalProperties": false
              }
            },
            "required": [
              "collection"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_record_store_permanently_delete_collection": {
        "type": "object",
        "properties": {
          "collection_id": {
            "type": "string"
          }
        },
        "required": [
          "collection_id"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_record_store_permanently_delete_collection": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "properties": {
              "deleted": {
                "type": "boolean",
                "const": true
              },
              "collection_id": {
                "type": "string"
              }
            },
            "required": [
              "deleted",
              "collection_id"
            ],
            "additionalProperties": false
          }
        }
      },
      "ActionPlatformOperationRequest_m365_list_authorized_senders": {
        "type": "object",
        "properties": {},
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_m365_list_authorized_senders": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "additionalProperties": false,
            "required": [
              "senders"
            ],
            "properties": {
              "senders": {
                "type": "array",
                "items": {
                  "type": "object",
                  "additionalProperties": false,
                  "required": [
                    "sender_id",
                    "type",
                    "display_name",
                    "email",
                    "available",
                    "recommended_use",
                    "interactive_eligible",
                    "scheduled_eligible"
                  ],
                  "properties": {
                    "sender_id": {
                      "type": "string",
                      "description": "Stable sender identifier. Use only values returned by discovery."
                    },
                    "type": {
                      "type": "string",
                      "enum": [
                        "member_mailbox",
                        "shared_mailbox"
                      ]
                    },
                    "display_name": {
                      "type": "string"
                    },
                    "email": {
                      "type": "string",
                      "format": "email"
                    },
                    "available": {
                      "type": "boolean"
                    },
                    "recommended_use": {
                      "type": "string"
                    },
                    "interactive_eligible": {
                      "type": "boolean"
                    },
                    "scheduled_eligible": {
                      "type": "boolean"
                    }
                  }
                }
              }
            }
          }
        }
      },
      "ActionPlatformOperationRequest_m365_list_send_history": {
        "type": "object",
        "properties": {},
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_m365_list_send_history": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "additionalProperties": false,
            "required": [
              "entries"
            ],
            "properties": {
              "entries": {
                "type": "array",
                "items": {
                  "type": "object",
                  "additionalProperties": false,
                  "required": [
                    "operation_id",
                    "actor_user_id",
                    "workspace_id",
                    "logged_at",
                    "status",
                    "view"
                  ],
                  "properties": {
                    "operation_id": {
                      "type": "string",
                      "const": "m365.send_email"
                    },
                    "actor_user_id": {
                      "type": "string"
                    },
                    "workspace_id": {
                      "type": "string"
                    },
                    "logged_at": {
                      "type": "string"
                    },
                    "status": {
                      "type": "string",
                      "enum": [
                        "ok",
                        "denied",
                        "failed"
                      ]
                    },
                    "operation_approval_id": {
                      "type": "string"
                    },
                    "routine_grant_id": {
                      "type": "string"
                    },
                    "automation_grant_id": {
                      "type": "string"
                    },
                    "view": {
                      "type": "object",
                      "additionalProperties": true
                    }
                  }
                }
              }
            }
          }
        }
      },
      "ActionPlatformOperationRequest_m365_send_email": {
        "type": "object",
        "properties": {
          "sender_id": {
            "type": "string",
            "description": "Stable sender_id from m365.list_authorized_senders. Optional for interactive calls (defaults to the Member mailbox); required for scheduled calls."
          },
          "connection_id": {
            "type": "string",
            "description": "Deprecated client hint. Interactive prepare/execute always bind and verify the Member's live Microsoft 365 connection server-side; a client-supplied value never authorizes alone."
          },
          "to": {
            "type": "array",
            "minItems": 1,
            "maxItems": 20,
            "items": {
              "type": "string",
              "format": "email"
            }
          },
          "cc": {
            "type": "array",
            "maxItems": 20,
            "items": {
              "type": "string",
              "format": "email"
            }
          },
          "subject": {
            "type": "string",
            "minLength": 1,
            "maxLength": 255
          },
          "body": {
            "type": "string",
            "minLength": 1,
            "maxLength": 100000,
            "description": "Plain-text email body."
          },
          "output_definition": {
            "type": "string",
            "minLength": 1,
            "maxLength": 200,
            "description": "Required for scheduled calls: exact Procedure or output definition bound by the Routine Grant."
          },
          "idempotency_key": {
            "type": "string",
            "minLength": 1,
            "maxLength": 200,
            "description": "Stable caller-generated key so retries return the original submission outcome without a second Graph send. When omitted, interactive calls use the issued approval identifier and scheduled calls use x-routine-invocation-id."
          },
          "confirm_send": {
            "type": "boolean",
            "const": true,
            "description": "Deprecated compatibility flag. Must be true when supplied; it never authorizes execution by itself. Interactive sends require a payload-bound operation approval."
          }
        },
        "required": [
          "to",
          "subject",
          "body"
        ],
        "additionalProperties": false
      },
      "ActionPlatformOperationResponse_m365_send_email": {
        "type": "object",
        "required": [
          "result"
        ],
        "additionalProperties": false,
        "properties": {
          "result": {
            "type": "object",
            "additionalProperties": false,
            "required": [
              "integration",
              "action",
              "status",
              "sender_id",
              "sender_type",
              "recipientCount",
              "idempotency_key"
            ],
            "properties": {
              "integration": {
                "type": "string",
                "const": "microsoft_365"
              },
              "action": {
                "type": "string",
                "const": "send_email"
              },
              "status": {
                "type": "string",
                "enum": [
                  "accepted",
                  "failed",
                  "unknown"
                ],
                "description": "Submission state only. accepted means Graph accepted the message for processing; never claims sent or delivered. unknown means the outcome is ambiguous — do not submit a second message with a new key."
              },
              "sender_id": {
                "type": "string"
              },
              "sender_type": {
                "type": "string",
                "enum": [
                  "member_mailbox",
                  "shared_mailbox"
                ]
              },
              "recipientCount": {
                "type": "integer",
                "minimum": 1
              },
              "idempotency_key": {
                "type": "string",
                "description": "Idempotency key used for this submission (caller-supplied, approval, or scheduled invocation id)."
              },
              "graph_correlation": {
                "type": "object",
                "additionalProperties": false,
                "description": "Safe Graph correlation retained for audit and support; never includes message bodies.",
                "properties": {
                  "graph_request_id": {
                    "type": "string"
                  },
                  "graph_client_request_id": {
                    "type": "string"
                  },
                  "http_status": {
                    "type": "integer"
                  }
                }
              }
            }
          }
        }
      }
    }
  }
}
```
