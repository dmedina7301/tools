#ARG BASE_REGISTRY=registry1.dso.mil
#ARG BASE_IMAGE=ironbank/carnegie-mellon/jlab-dl
#ARG BASE_TAG=3.6
#FROM ${BASE_REGISTRY}/${BASE_IMAGE}:${BASE_TAG}

FROM afcai2c/jlab-dl:latest

USER root

RUN yum update -y -q && \
    yum install -y -q   \
    mesa-libGL

RUN python3.6 -m pip install \
    opencv-python            \
    imutils                  \
    pytesseract              \
    pytorchcv                \
    scikit-image

USER jovyan

WORKDIR $HOME

ENTRYPOINT ["tini", "-g", "--"]
CMD ["start-notebook.sh"]

EXPOSE 8888

HEALTHCHECK --interval=10s --timeout=1s CMD python.3.6 -c 'print("up")' || exit 1


