CREATE DATABASE gestion_tercera_edad;
USE gestion_tercera_edad;

CREATE TABLE Residente (
    id_residente INT AUTO_INCREMENT PRIMARY KEY,
    nombre       VARCHAR(100) NOT NULL,
    fecha_nac    DATE NOT NULL
);

CREATE TABLE Historial (
    id_historial INT AUTO_INCREMENT PRIMARY KEY,
    id_residente INT NOT NULL,
    patologia    VARCHAR(150) NOT NULL,
    evolucion    TEXT,
    fecha        DATE NOT NULL,
    FOREIGN KEY (id_residente) REFERENCES Residente(id_residente)
);

CREATE TABLE Categoria (
    id_categoria INT AUTO_INCREMENT PRIMARY KEY,
    nombre       VARCHAR(80) NOT NULL
);

CREATE TABLE Proveedor (
    id_proveedor INT AUTO_INCREMENT PRIMARY KEY,
    nombre       VARCHAR(100) NOT NULL,
    telefono     VARCHAR(20)
);

CREATE TABLE Insumo (
    id_insumo    INT AUTO_INCREMENT PRIMARY KEY,
    nombre       VARCHAR(100) NOT NULL,
    id_categoria INT NOT NULL,
    stock_min    INT NOT NULL DEFAULT 0,
    FOREIGN KEY (id_categoria) REFERENCES Categoria(id_categoria)
);

CREATE TABLE Medicamento (
    id_medicamento   INT AUTO_INCREMENT PRIMARY KEY,
    id_insumo        INT NOT NULL,
    principio_activo VARCHAR(100) NOT NULL,
    forma            VARCHAR(50),
    FOREIGN KEY (id_insumo) REFERENCES Insumo(id_insumo)
);

CREATE TABLE Lote (
    id_lote      INT AUTO_INCREMENT PRIMARY KEY,
    id_insumo    INT NOT NULL,
    id_proveedor INT NOT NULL,
    cantidad     INT NOT NULL,
    vence        DATE,
    FOREIGN KEY (id_insumo)    REFERENCES Insumo(id_insumo),
    FOREIGN KEY (id_proveedor) REFERENCES Proveedor(id_proveedor)
);

CREATE TABLE Prescripcion (
    id_prescripcion INT AUTO_INCREMENT PRIMARY KEY,
    id_residente    INT NOT NULL,
    id_medicamento  INT NOT NULL,
    dosis           VARCHAR(50) NOT NULL,
    FOREIGN KEY (id_residente)   REFERENCES Residente(id_residente),
    FOREIGN KEY (id_medicamento) REFERENCES Medicamento(id_medicamento)
);

CREATE TABLE Movimiento (
    id_movimiento INT AUTO_INCREMENT PRIMARY KEY,
    id_lote       INT NOT NULL,
    id_residente  INT NULL,
    tipo          ENUM('entrada','salida') NOT NULL,
    cantidad      INT NOT NULL,
    fecha         DATE NOT NULL,
    FOREIGN KEY (id_lote)      REFERENCES Lote(id_lote),
    FOREIGN KEY (id_residente) REFERENCES Residente(id_residente)
);
