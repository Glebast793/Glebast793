using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class cybe : MonoBehaviour
{
    public LayerMask layerMask;
    [Header("Скорость героя")] ///заголовок 
    [SerializeField]
    [Range(0f, 100f)]
    private int _speed;
    [Header("Сила прыжка")]
    [SerializeField]
    [Range(0f, 100f)] ///длябегункаот0до100 
    private int _JumpForce;
    void Update()
    {
        float moveHorizontal = Input.GetAxis("Horizontal");
        float moveVertical = Input.GetAxis("Vertical");

        Vector3 movement = new Vector3(moveHorizontal, 0.0f, moveVertical).normalized;
        transform.Translate(movement * _speed * Time.deltaTime);

        RaycastHit hit;

        if (Physics.Raycast(transform.position, transform.forward, out hit, Mathf.Infinity, layerMask))
        {
            Debug.Log("Object on layer " + LayerMask.LayerToName(hit.transform.gameObject.layer) + " detected!");
        }
    }
}

   
